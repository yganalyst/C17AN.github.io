---
title:  "[Java] - SharedPreference 사용하기"
search: true
toc : true
toc_label : 네비게이션
header:
  teaser: "/assets/images/header/android.png"
toc_sticky : true
tag:
  - Java
  - android
categories:
  - Java
excerpt: "[Java] - 간단한 저장소인 SharedPreference 활용하기"
last_modified_at: 2020-05-01T08:06:00-05:00
---
## 1. 🥾 SharedPreference 객체   

데이터 중에 앱을 종료한 후에도 남아있어야 하되, 굳이 DB에 올릴 필요까지는 없는 것도 있을 것이다. (Ex. 🎮 싱글게임 최고기록 등?)    

**SharedPreference** 는 입력값 등 작은 데이터를 마치 캐시처럼 내부 저장소에 **xml** 파일로 저장해두었다가 사용할 수 있게 해준다.   

---

SharedPreferences 의 기본 원리는 이렇다.   

- 앱 종료시 값을 임시 저장소에 저장
- 앱 실행 시 임시 저장소에서 값 인출

간단하게 그냥 작은 깃 저장소를 하나 만들고 깃 저장소를 이용하는 과정이라고 생각하면 된다.

---

## 2. 👟 SharedPreference 객체를 사용해 값 임시 저장하기   

우선 어플리케이션 생명주기에 대한 간단한 이해가 필요한데, **onCreate** 메서드와 **onDestroy** 메서드는 각각 앱이 실행될 때 / 종료될 때 실행되는 메서드이다.   

따라서, onDestroy 메서드에서 우리가 저장할 값을 sharedPreferences 를 사용해 저장하고 onCreate 메서드에서는 이를 가져오도록 하면 된다.

---

- **액티비티 : MainActivity**
- **MainActivity : EditText 폼에서 텍스트를 입력받고 보관하기**
- **앱을 종료하고 재실행해도 입력값이 남아있도록 만들기**

---

**MainActivity.java**
{: .notice--info}

```java
public class MainActivity extends AppCompatActivity {

    EditText et_save; // 텍스트 입력란

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
        et_save = findViewById(R.id.et_save);
        SharedPreferences sharedPreferences = getSharedPreferences("file", 0);
        String value = sharedPreferences.getString("data", "");
        et_save.setText(value);
    }

    @Override
    protected void onDestroy() {
        // 액티비티를 벗어났을 때 실행되는 생명주기
        super.onDestroy();
        SharedPreferences sharedPreferences = getSharedPreferences("file", 0);
        SharedPreferences.Editor editor = sharedPreferences.edit();
        String value = et_save.getText().toString();
        editor.putString("data", value); // alias - value
        editor.commit(); // 변경사항 저장
    }
}
```

---

## 3. 👞 onDestroy 부분

앱이 종료될 때, 내가 원하는 데이터를 저장소에 저장해야 한다.   

---

```java

protected void onDestroy() {
  // ... 생략
  super.onDestroy();
  SharedPreferences sharedPreferences = getSharedPreferences("file", 0);
  // ... 생략
}
```

---

우선 getSharedPreferences() 함수에서는 값을 실제로 저장할 xml 파일을 불러오고 저장할 모드를 지정한다.    
이 때, 만약 지정한 파일명을 가진 파일이 없다면 해당 파일명으로 된 xml 파일을 생성한다.

|저장 모드|설명|
|:-:|:-:|
|MODE_PRIVATE|현재 앱에서만 접근 가능|
|MODE_WORLD_READABLE|다른 앱에서 읽기 가능|  
|MODE_WORLD_WRITABLE|다른 앱에서 쓰기 가능|

예를 들어 ("file", 0) 을 매개변수로 주면 file.xml 파일을 생성해 그 안에 데이터를 저장하고, 해당 앱에서만 데이터의 접근을 허용한다.   
그 후 SharedPreference 객체를 통해 해당 파일에 I/O를 수행한다.

---

그 후 Editor 라는 생소한 객체가 등장하는데, 간단하게 작은 git 이라고 생각하면 된다.

---

```java
SharedPreferences.Editor editor = sharedPreferences.edit();
```

---

Editor 에 값을 저장하기 위해 SharedPreferences (* 실제로는 xml 파일) 객체의 메서드 중 edit() 메서드를 사용해 입력을 시작한다.   

---

```java
editor.putString("data", value); // alias - value
editor.commit(); // 변경사항 저장
```

---

다음으로 Editor 에 실제 값을 입력하기 위해서는 Editor 의 putString 메서드를 이용하는데, SharedPreference 파일은 `키-값` 형태로 데이터를 저장하므로 putString() 의 매개변수로는 키로 사용될 별명과 실제 값을 준다.   

그렇게 Editor 에 수정사항이 발생했다면, commit 메서드를 통해 수정을 마칠 수 있다.   
이제 앱이 종료될 때 우리가 정한 키-값 쌍의 데이터가 담긴 xml 파일이 완성된다. 😄   

---

## 4. 👾 onCreate 부분

앱이 다시 실행될 때 onDestroy 부분에서 만들었던 데이터를 가져오려면 역시 getSharedPreferences() 메서드를 사용한다.

---

```java
protected void onCreate(Bundle savedInstanceState) {
    super.onCreate(savedInstanceState);
    SharedPreferences sharedPreferences = getSharedPreferences("file", 0);
    String value = sharedPreferences.getString("data", "");
}
```

---

onDestroy() 단계에서 만들었던 xml 파일명을 불러온 후, 파일에 존재하는 데이터를 지정한 별명(키) 를 통해 접근한다.  

getString() 메서드의 매개변수로는 xml 파일 내 키와 해당 키가 존재하지 않을 경우 기본으로 반환할 값을 지정한다.   

---

**👨‍💻 실행 결과**
{: .notice--info}

<img src = "/assets/images/2020-05-01-SharedPreferences/실행화면.gif" width = "400">

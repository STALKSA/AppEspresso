### Добавление зависимостей

1. Открыть файл /app/build.gradle.
2. Проверить наличие и при необходимости добавить зависимости в блок «dependencies»:
```java
     testImplementation 'junit:junit:4.13.2' 
     androidTestImplementation 'androidx.test.ext:junit:1.1.3' 
     androidTestImplementation 'androidx.test:rules:1.4.0'  
     androidTestImplementation 'androidx.test:runner:1.4.0' 
     androidTestImplementation 'androidx.test.espresso:espresso-core:3.4.0' 
```

### Создание и настройка класса тестов

1. Создать новый класс в директории /app/src/androidTest/java/ru/kkuzmichev/simpleappforespresso/.
2. Добавить @RunWith(AndroidJUnit4.class) над именем класса.
3. Задать правило для MainActivity внутри класса:
```java
@Rule
public ActivityTestRule<MainActivity> activityTestRule =
	new ActivityTestRule<>(MainActivity.class);
```

### Написание теста

1. Запустить приложение.
2. Построить иерархию элементов с помощью Layout Inspector: [инструкция от Google](https://developer.android.com/studio/debug/layout-inspector).
3. Найти элемент с текстом «This is home fragment» и его ID.
4. Написать тест, проверяющий, что у найденного ID текст «This is home fragment».

Шаблон теста:
```java
@Test
public void testName() {
    ViewInteraction mainText = onView(
        withId(R.id.найденный id)
    );
    mainText.check(
        matches(
            withText(Проверяемый текст)
        )
    );
}
```

### Запуск теста и просмотр отчёта

1. Запустить тест, нажав кнопку запуска возле метода теста.
2. Проверить, что тест прошёл успешно.
3. Экспортировать отчёт в html-файл. 

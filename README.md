# Інтеграція Creatio з HTML сторінкою

Цей репозиторій містить інтеграційний код для лендингової сторінки

## Використання

1. Вставте наступні скрипти у вашу HTML-строрінку, перед тегом `</body>`:

```html
<script src="https://ajax.googleapis.com/ajax/libs/jquery/1.11.2/jquery.min.js"></script>
<script src="https://webtracking-v01.bpmonline.com/JS/track-cookies.js"></script>
<script src="https://webtracking-v01.bpmonline.com/JS/create-object.js"></script>
<script>
// --Ваш JavaScript-код тут--
</script>
```

2. 1. Замініть вираз в лапках "css-selector" в коді нижче значенням селектора елемента на Вашій лендінговій сторінці. 
   3. Ви можете використати #id або будь-який інший CSS селектор, який буде точно визначати поле вводу на Вашій лендінговій сторінці.
   4. **Приклад:** "Email": "#MyEmailField" або "Name": ".form-join .modal-name"
   5. Замініть **landingId** та **serviceUrl** на ті що згенеровані системою
   

```javascript
var config = {
    fields: {
        "Name": "css-selector", // Имя визитера
        "Email": "css-selector", // Email визитера
        "MobilePhone": "css-selector", // Телефон визитера
        "Company": "css-selector", // Название компании
        "Industry": "css-selector", // Отрасль компании
        "FullJobTitle": "css-selector", // Должность визитера
        "Commentary": "css-selector" // Примечание
    },
    contactFields: {},
    customFields: {},
    landingId: "207c87df-934a-4737-8d8b-050ecaf0facf",
    serviceUrl: "https://1137971-demo.creatio.com/0/ServiceModel/GeneratedObjectWebFormService.svc/SaveWebFormObjectData",
    redirectUrl: ""
};
```
Замініть `--Ваш JavaScript-код тут--` на налаштований код для сторінку лендінга

3. Функція нижче створює об'єкт із введених даних.
* Прив'яжіть виклик цієї функції до події "onSubmit" форми або будь-якому іншому елементу події.
* Приклад: 
```<form class="mainForm" name="landingForm" onSubmit="createObject(); return false">```

```javascript
function createObject() {
    landing.createObjectFromLanding(config);
}

/* Функція нижче ініціює лендинг з параметрів URL. */
function initLanding() {
    landing.initLanding(config);
}

jQuery(document).ready(initLanding);
```

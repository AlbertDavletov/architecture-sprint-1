# Задание 1

## Уровень 1. Проектирование
Данных по проекту Mesto и его планам недостаточно, чтобы принять правильное решение относительно технологий. Поэтому будем считать, что требуется сделать POC приложения, используя разбивку на микросервисы. 
Для простоты будем использовать React во всех микросервисах. Поэтому нет особой нужны в SPA, воспользуемся конфигурацией Webpack Module Federation.

## Уровень 2. Планирование изменений
У нас нет информации о составе команды Mesto, а также нет строгих требований по изоляции микросервисов. Поэтому идеальным вариантом будет разбивка по бизнес функциям, то есть вертикальная нарезка.

### Сервисы:
- Сервис авторизации: форма логина и регистрации/
- Сервис карточек: страница с фото карточками с функциями удаления, добавления и лайков.
- Сервис профиля пользователя: форма профиля с функциями редактирования имени и аватарки пользователя.
- Хост приложения.

### Управление состоянием
- Для простоты в данном POC использовалась модель событийная модель Pub/Sub. Однако более правильным решением будет использование глобального состояния, в данном случае библиотеки Redux. В данном приложении все микросервисы тесно связаны, поэтому использование глобальных значений более оптимально. Например, во всех сервисах необходимо использовать значение (email, token) текущего пользователя.

### Структура
microfrontend
 - auth
 	- blocks (styles)
 	- components
 		- login.js
 		- register.js
 	- utils
 		- auth-api.js
 	- webpack.config.js
 	- package.json
 - profile
  	- blocks (styles)
 	- components
 		- editAvatarPopup.js
 		- editProfilePopup.js
 		- profile.js
 	- utils
 		- api.js
 	- webpack.config.js
 	- package.json
 - photos
  	- blocks (styles)
 	- components
 		- addPlacePopup.js
 		- imagePopup.js
 		- card.js
 		- cards.js
 	- utils
 		- api.js
 	- webpack.config.js
 	- package.json
 - host
  	- blocks (styles)
 	- components
 		- App.js
 		- footer.js
 		- header.js
 		- infoTooltip.js
 		- main.js
 		- protectedRoute.js
 	- images
 	- webpack.config.js
 	- package.json 	

### Дополнительные сервисы на будущее:
- Сервис общих контролов и утилит: кастомные контролы общие для всех микросервисов или общие утилиты. Например, базовый контрол для всплывающего окна, а также контрол Header, Footer.
- Сервис лайков: на сайте напрашивается раздел с видео контентом, где также понадобится функционал лайков, который можно будет вынести в отдельный сервис.

## Уровень 3. Запуск готового кода
Запуск приложения Mesto:
- cd frontend/microfrontend/host && npm start:all
```
"start:all": "concurrently \"cd ../auth && npm install && npm start\" \"cd ../photos && npm install && npm start\" \"cd ../profile && npm install && npm start\" \"cd ../host && npm install && npm start\""
```

# Задание 2
TODO
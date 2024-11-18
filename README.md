1. В проекте используется Module Federation. Я выбрала его, поскольку у нас используется 1 фреймворк, и тк в примере был разобран случай с этим тулом. 

2. Данный проект я разбила на 4 микросервиса по DDD: 
* autorization-microfrontend занимается аунтификацией и авторизацией.
* users-microfrontend используется для работы с данными пользователя: информацией о нем и аватаре.
* cards-microfrontend используется для работы с карточками: добавление, удаление, лайки, просмотр в окне, редактирование.
* host-microfrontend используется как входная точка приложения: он формирует главную страницу, организует работу приложения, делегирует задачи остальным микрофронтендам.

Также добавила библиотеку library, где вынесены общие для разных микрофронтендов элементы. В package.json фронтов, которые ею пользуются, должна будет добавлена соответствующая зависимость.

Структуру проекта вместе со всеми файлами указала ниже в виде дерева. Маршрутизация не настроена.
Компоненты, стили, апи, картинки -- все было перенесено в соответствующие микрофронтенды.

PS для корректного форматирования в браузере лучше смотреть сырой файл (например, перейти в редактирование)  
.  
├── authorization-microfrontend  
│   └── src  
│       ├── App.jsx  
│       ├── blocks  
│       │   ├── auth-form  
│       │   │   ├── __button  
│       │   │   │   └── auth-form__button.css  
│       │   │   ├── __form  
│       │   │   │   └── auth-form__form.css  
│       │   │   ├── __input  
│       │   │   │   └── auth-form__input.css  
│       │   │   ├── __link  
│       │   │   │   └── auth-form__link.css  
│       │   │   ├── __text  
│       │   │   │   └── auth-form__text.css  
│       │   │   ├── __textfield  
│       │   │   │   └── auth-form__textfield.css  
│       │   │   ├── __title  
│       │   │   │   └── auth-form__title.css  
│       │   │   └── auth-form.css  
│       │   └── login  
│       │       └── login.css  
│       ├── components  
│       │   ├── InfoTooltip.js  
│       │   ├── Login.js  
│       │   └── Register.js  
│       ├── contexts  
│       ├── images  
│       │   ├── error-icon.svg  
│       │   └── success-icon.svg  
│       ├── index.css  
│       ├── index.js  
│       ├── logo.svg  
│       ├── package.json  
│       ├── serviceWorker.js  
│       ├── setupTests.js  
│       ├── utils  
│       │   └── auth.js  
│       ├── vendor  
│       └── webpack.config.js  
├── cards-microfrontend  
│   └── src  
│       ├── App.jsx  
│       ├── blocks  
│       │   ├── card  
│       │   │   ├── __delete-button  
│       │   │   │   ├── _hidden  
│       │   │   │   │   └── card__delete-button_hidden.css  
│       │   │   │   ├── _visible  
│       │   │   │   │   └── card__delete-button_visible.css  
│       │   │   │   └── card__delete-button.css  
│       │   │   ├── __description  
│       │   │   │   └── card__description.css  
│       │   │   ├── __image  
│       │   │   │   └── card__image.css  
│       │   │   ├── __like-button  
│       │   │   │   ├── _is-active  
│       │   │   │   │   └── card__like-button_is-active.css  
│       │   │   │   └── card__like-button.css  
│       │   │   ├── __like-count  
│       │   │   │   └── card__like-count.css  
│       │   │   ├── __title  
│       │   │   │   └── card__title.css  
│       │   │   └── card.css  
│       │   └── places  
│       │       ├── __item  
│       │       │   └── places__item.css  
│       │       ├── __list  
│       │       │   └── places__list.css  
│       │       └── places.css  
│       ├── components  
│       │   ├── AddPlacePopup.js  
│       │   ├── Card.js  
│       │   └── ImagePopup.js  
│       ├── contexts  
│       ├── images  
│       │   ├── card_1.jpg  
│       │   ├── card_2.jpg  
│       │   ├── card_3.jpg  
│       │   ├── delete-icon.svg  
│       │   ├── like-active.svg  
│       │   └── like-inactive.svg  
│       ├── index.css  
│       ├── index.js  
│       ├── logo.svg  
│       ├── package.json  
│       ├── serviceWorker.js  
│       ├── setupTests.js  
│       ├── utils  
│       │   └── api.js  
│       └── webpack.config.js  
├── host-microfrontend  
│   └── src  
│       ├── App.jsx  
│       ├── blocks  
│       │   ├── footer  
│       │   │   ├── __copyright  
│       │   │   │   └── footer__copyright.css  
│       │   │   └── footer.css  
│       │   ├── header  
│       │   │   ├── __auth-link  
│       │   │   │   └── header__auth-link.css  
│       │   │   ├── __logo  
│       │   │   │   └── header__logo.css  
│       │   │   ├── __logout  
│       │   │   │   └── header__logout.css  
│       │   │   ├── __user  
│       │   │   │   └── header__user.css  
│       │   │   ├── __wrapper  
│       │   │   │   └── header__wrapper.css  
│       │   │   └── header.css  
│       │   └── page  
│       │       ├── __content  
│       │       │   └── page__content.css  
│       │       ├── __section  
│       │       │   └── page__section.css  
│       │       └── page.css  
│       ├── components  
│       │   ├── App.js  
│       │   ├── Footer.js  
│       │   ├── Header.js  
│       │   ├── Main.js  
│       │   └── ProtectedRoute.js  
│       ├── contexts  
│       │   └── CurrentUserContext.js  
│       ├── images  
│       │   └── logo.svg  
│       ├── index.css  
│       ├── index.js  
│       ├── logo.svg  
│       ├── package.json  
│       ├── serviceWorker.js  
│       ├── setupTests.js  
│       ├── utils  
│       │   └── api.js  
│       └── webpack.config.js  
├── index.spec.js  
├── library  
│   └── common  
│       └── src  
│           ├── blocks  
│           │   ├── content  
│           │   │   └── content.css  
│           │   └── popup  
│           │       ├── __button  
│           │       │   ├── _disabled  
│           │       │   │   └── popup__button_disabled.css  
│           │       │   └── popup__button.css  
│           │       ├── __caption  
│           │       │   └── popup__caption.css  
│           │       ├── __close  
│           │       │   └── popup__close.css  
│           │       ├── __content  
│           │       │   ├── _content  
│           │       │   │   └── popup__content_content_image.css  
│           │       │   └── popup__content.css  
│           │       ├── __error  
│           │       │   ├── _visible  
│           │       │   │   └── popup__error_visible.css  
│           │       │   └── popup__error.css  
│           │       ├── __form  
│           │       │   └── popup__form.css  
│           │       ├── __icon  
│           │       │   └── popup__icon.css  
│           │       ├── __image  
│           │       │   └── popup__image.css  
│           │       ├── __input  
│           │       │   ├── _type  
│           │       │   │   └── popup__input_type_error.css  
│           │       │   └── popup__input.css  
│           │       ├── __label  
│           │       │   └── popup__label.css  
│           │       ├── __status-message  
│           │       │   └── popup__status-message.css  
│           │       ├── __title  
│           │       │   └── popup__title.css  
│           │       ├── _is-opened  
│           │       │   └── popup_is-opened.css  
│           │       ├── _type  
│           │       │   ├── popup_type_edit-avatar.css  
│           │       │   └── popup_type_remove-card.css  
│           │       └── popup.css  
│           ├── components  
│           │   └── PopupWithForm.js  
│           ├── images  
│           │   └── close.svg  
│           └── vendor  
│               ├── fonts  
│               │   ├── Inter-Black.woff2  
│               │   └── Inter-Regular.woff2  
│               ├── fonts.css  
│               └── normalize.css  
├── microfrontend  
├── package-lock.json  
├── package.json  
├── public  
│   ├── favicon.ico  
│   ├── index.html  
│   ├── logo192.png  
│   ├── logo512.png  
│   ├── manifest.json  
│   └── robots.txt  
├── src  
│   ├── blocks  
│   ├── components  
│   ├── contexts  
│   ├── images  
│   ├── index.css  
│   ├── index.js  
│   ├── logo.svg  
│   ├── serviceWorker.js  
│   ├── setupTests.js  
│   ├── utils  
│   │   └── api.js  
│   └── vendor  
└── users-microfrontend  
    └── src  
        ├── App.jsx  
        ├── blocks  
        │   └── profile  
        │       ├── __add-button  
        │       │   └── profile__add-button.css  
        │       ├── __description  
        │       │   └── profile__description.css  
        │       ├── __edit-button  
        │       │   └── profile__edit-button.css  
        │       ├── __image  
        │       │   └── profile__image.css  
        │       ├── __info  
        │       │   └── profile__info.css  
        │       ├── __title  
        │       │   └── profile__title.css  
        │       └── profile.css  
        ├── components  
        │   ├── EditAvatarPopup.js  
        │   └── EditProfilePopup.js  
        ├── contexts  
        ├── images  
        │   ├── add-icon.svg  
        │   ├── avatar.jpg  
        │   └── edit-icon.svg  
        ├── index.css  
        ├── index.js  
        ├── logo.svg  
        ├── package.json  
        ├── serviceWorker.js  
        ├── setupTests.js  
        ├── utils  
        │   └── api.js  
        └── webpack.config.js  

Задание 1
В качестве фреймворка для разделения приложения был выбран Module Federaion, одной из причин было то, 
что все приложение написано на одном языке с использованием одного стека - JS/TS
SingleSPA все же больше для более глобального объединения разных архитектур и технологий
В данном примере небольшое приложение,  и для объединения компонентов как раз подойдет Module Federaion

Дополнительно отмечу, что у меня нулевой опыт работы с фронтом и языками JavaScript\Typescript, а в курсе были примеры
с использованием именно Module Federaion, т.е. сюда еще можно отнести "опыт команды разработки" (0.01% MF vs 0% JPA)

Приложение фронтенда было разделено на 3 основных компонента:

1. auth-microfrontend - сервис аутентификации и авторизации 

  /src
    /components
      Login.js               // Компонент входа пользователя
      Register.js            // Компонент регистрации пользователя
	  InfoTooltip.js		 // Информация о статусе регистрации		
    /styles					 // необходимые стили для форм авторизации/аутентификации 
(некоторые, например content, page будут продублированы в других модулях чтобы сделать их изолированными)
       auth-form
	   content	
	   login
	   page
	   popup
		
    /utils
      auth.js                // Утилиты для аутентификации
    index.js                 // Точка входа микрофронтенда
	package.json             // Зависимости и скрипты микрофронтенда
	webpack.config.js	     // добавлен модуль Module Federaion



2. profile-microfrontend - личный кабинет пользователя

  /src
    /components
      EditAvatarPopup.js               // Компонент добавления/замены аватара пользователя
      EditProfilePopup.js              // Компонент редактирования профиля (имя/фамилия/профессия) 



3. card-microfrontend - модуль с основным функционалом по работе с картинками (добавление/удаление/подсчет лайков)
  /src
    /components
      Card.js               // Компонент "корзины"  (каталог всех фото пользователя)
      ImagePopup.js         // функционал открытия/загрузки картинки
	  PopupWithForm.js	    // компонет работы с картинками и меню
	  AddPlacePopup.js		// компонет работы с картинками и меню
	/contexts
	  CurrentUserContext.js	//Объект контекста CurrentUserContext экспортируется из отдельного файла директории contexts (не знаю зачем это сделано, но предполагаю что относится к объекту каталога фото)
	/images  // каталог картинок для работы модуля /card - рабочие иконки для кнопок
	/styles  //необходимые стили для форм
	

Так же я попытался поменять основное приложение App.js 	и заменить создание функций на их иморты функций на примере onLogin/onRegister
но т.к. у меня нет опыта и знаний работы c JavaScript уверен что сделал это неверно (пытался повторить опыт из примера спринта)
Добавил в каждый микрофонтенд webpack.config.js и в нем прописан плагин ModuleFederationPlugin с указанием локальных модулей микрофронтедов



Задание 2:
ссылка на схему
https://viewer.diagrams.net/?tags=%7B%7D&lightbox=1&highlight=0000ff&edit=_blank&layers=1&nav=1#G1MsJ82nx4z0b1-QYDSjEqg0a54gfnobaV
продублирую на диске:
https://drive.google.com/file/d/1MsJ82nx4z0b1-QYDSjEqg0a54gfnobaV/view


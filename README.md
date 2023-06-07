# RabbitMQ-and-ASP.NET-Core
RabbitMQ в проектах ASP.NET Core 
Использование  RabbitMQ в проектах ASP.NET Core

Создадим 2 проекта ASP.NET Core Web API: проект, который будет поставщиком (продюсером) сообщений, и проект, который будет подписчиком (консьюмером).

Для обоих проектов, после их создания на последующих шагах, необходимо выполнить установку NuGet пакета: RabbitMQ.Client.
1. Создаем проект ASP.NET Core Web API с продьюсером.
Запустим проект Producer, и в сваггере (https://localhost:ваш_порт/swagger/index.html) вызовем метод SendMessage, передав в качестве параметра произвольную строку. Для этого нажмем на строке этого метода, в открывшейся панели вверху справа нажмем кнопку Try it out, и в окне message введем наше сообщение. Нажмем кнопку Execute.

В ответе мы должны получить статус код 200 и сообщение “Сообщение отправлено”.

Если вы используете локальный сервер RabbitMQ, переходим в панель управления локальным экземпляром RabbitMQ (http://localhost:15672).

Перейдем на вкладку Queues, в табличке нажмем на наименовании нашей очереди ("MyQueue").

В списке внизу раскроем элемент Get messages, нажмем кнопку Get message(s), и увидим наше сообщение.

Продюсер работает. 

2. Создаем проект ASP.NET Core Web API с консьюмером. 

В Visual Studio создаем новый проект ASP.NET Core Web API.

В новый проект добавляем NuGet пакет RabbitMQ.Client.
В данном примере мы создали консьюмер для локального сервера RabbitMQ:

var factory = new ConnectionFactory() { HostName = "localhost" };

Запустим оба проекта – продюсер и консьюмер.

Перейдем в сваггер продюсера, и отправим произвольное сообщение.

В окне Output from Debug появится наше сообщение, выведенное методом

Debug.WriteLine($"Получено сообщение: {content}");
нашего консьюмера.

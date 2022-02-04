---
description: Создаем первую игру с простой физикой и управлением
---

# 🕹 Занятие 2: первая игра - Roll a Ball

{% hint style="warning" %}
Перед началом смотри [создание проекта](./#sozdanie-svoego-pervogo-proekta)
{% endhint %}

## Идея

Сделаем простую игру где можно будет двигать шар :soccer: по горизонтали и вертикали чтобы подбирать раскиданные по локации кубики :ice\_cube: и ограничить его передвижение стенами.

## Создание уровня

Нам нужно создать на сцене несколько кубов, трансформировать их и расставить их по уровню

{% hint style="info" %}
Сцена - это контейнер, в котором находятся все игровые объекты на уровне
{% endhint %}

По умолчанию у нас уже открыта сцена под названием <mark style="color:green;">SampleScene.</mark>\
Все объекты на сцене в виде иерархии можно увидеть в окне Hierarhy в левой части экрана, там уже создано два объекта: <mark style="color:green;">Main Camera</mark> (_камера, из которой игрок видит локацию_) и <mark style="color:green;">Directional Light</mark> (_глобальное освещение которое симулирует солнце в игре_).

![](<.gitbook/assets/image (23) (1).png>)

### Стены

Чтобы добавить новый объект на сцену нужно кликнуть правой кнопкой мыши в пустое место иерархии и выбрать какой именно объект хотим создать, в нашем случае <mark style="color:green;">3D Object -> Cube</mark>\
После этого куб появится не только в иерархии, но и на сцене\
Чтобы приблизиться к нему нужно выбрать его в иерархии и наведя мышь на окно <mark style="color:green;">Scene</mark> нажать клавишу <mark style="color:green;">**F**</mark>

![](<.gitbook/assets/image (22) (1).png>)

В данным момент выбран инструмент перемещения, который позволяет в помощью стрелок передвигать выбранный объект

Для изменения пропорций куба нужно выбрать инструмент <mark style="color:green;">Scale</mark> в верхней в части редактора

![](<.gitbook/assets/image (13) (1).png>)

Теперь при зажатие стрелок куб не перемещается, а расширяется в определенную сторону

Создадим еще 3 куба и сделаем замкнутую стену

{% hint style="info" %}
Чтобы дублировать выбранный объект нужно нажать <mark style="color:green;">Ctrl + D</mark>
{% endhint %}

Для вращения используется инструмент <mark style="color:green;">Rotate</mark>

![](<.gitbook/assets/image (1) (1).png>)

{% hint style="info" %}
Для поворота ровно на 15 градусов нужно зажать <mark style="color:green;">Ctrl</mark> во время вращения
{% endhint %}

Результат выглядит следующим образом:

![](<.gitbook/assets/image (24) (1).png>)

### Пол

Осталось только добавить пол: создадим объект 3D Object -> Plane, масштабируем его и переместим в центр

![](<.gitbook/assets/image (15) (1) (1).png>)

### Инспектор

Трансформировать объекты можно не только с помощью инструментов редактора, но и в окне инспектора

![](<.gitbook/assets/image (43).png>)

Помимо <mark style="color:green;">Transform</mark> объекта мы видим также другие компоненты: <mark style="color:green;">Renderer, Collider, Filter</mark>. Для чего они нужны мы рассмотрим позже. Важно запомнить что Transform есть на любом объекте и его нельзя убрать.

{% hint style="info" %}
Компонент - составная часть объекта, которая добавляет ему определенные возможность
{% endhint %}

Также в верхней части инспектора можно изменить и имя объекта, чтобы не путаться в большом количестве кубов\
Изменим названия объектов на сцене следующим образом:

![](<.gitbook/assets/image (12).png>)

### Сфера

Для начала добавим его на сцену <mark style="color:green;">3D Object -> Sphere</mark>

![](<.gitbook/assets/image (18).png>)

Теперь поменяем ей цвет, для этого потребуется создать новый материал в окне <mark style="color:green;">Project</mark> - там хранятся все ресурсы нашей игры (_модели, материалы, скрипты_). Для этого нужно начать правой кнопкой в любом свободном месте окна и выбрать Create -> Material\
После этого он появится в списке ресурсов проекта:

![](<.gitbook/assets/image (38).png>)

Выберем его и в Инспекторе поменяем цвет Albedo (_основная текстура_)

&#x20;

![](<.gitbook/assets/image (3).png>)

Для применения материала просто перетащим его на шар

![](<.gitbook/assets/image (16) (1) (1).png>)

Давайте рассмотрим набор компонентов сферы:

![](.gitbook/assets/image.png)

* <mark style="color:green;">Tranform</mark> - находится на любом объекте и служит для изменения положения, вращения и масштаба объекта
* <mark style="color:green;">Mesh Filter</mark> и <mark style="color:green;">Renderer</mark> - необходимы для фильтрации и построения исходного набора полигонов, который есть у каждой 3D модели, а также наложения материала на нее
* <mark style="color:green;">Sphere Collider</mark> - коллайдеры служат для просчета столкновений объектов и не позволяют им заходить друг в друга. Префикс Sphere означает что коллайдер сферической формы.

Однако если запустить игру, то все объекты находятся на своих местах, ничего не падает по физике и не сталкивается.

Для работы **физики** в Unity на конкретном объекте есть компонент <mark style="color:green;">Rigidbody</mark> - он необходим для работы гравитации, столкновений, а также триггеров.\
Чтобы его добавить в списке компонентов нажмем на кнопку <mark style="color:green;">Add Component</mark>, найти его в списке и выбрать. После этого он окажется на объекте с настройками по умолчанию

![](<.gitbook/assets/image (34) (1).png>)

![После запуска игры шар падает на пол под влиянием гравитации](<.gitbook/assets/image (22).png>)

### Камера

Однако если перейди во вкладку <mark style="color:green;">Game</mark> можно увидеть что камера направлена совсем не на сцену\
Чтобы направить камеру на нашу сцену можно либо использовать использовать инструменты вращения и перемещения

![](<.gitbook/assets/image (30).png>)

Либо же выровнять камеру в соответствии с обзором в окне Scene: для этого выберем камеру и в верхнем меню нажмем кнопку <mark style="color:green;">Object -> Align With View</mark>

После этого на вкладке <mark style="color:green;">Game</mark> обзор игрока будет следующим:

![](<.gitbook/assets/image (33).png>)

### Цели для игрока

По примеру выше вы должны создать небольшой куб с материалом <mark style="color:blue;"><mark style="color:purple;">синего<mark style="color:purple;"></mark> цвета

![](<.gitbook/assets/image (15) (1).png>)

## Введение в программирование

### Функции жизненного цикла MonoBehaviour

Это функции, который вызывает сам <mark style="color:green;">Unity</mark> у всех классов, которые наследуются от <mark style="color:green;">`MonoBehaviour`</mark>

#### `Awake`

Всегда вызывается перед функцией <mark style="color:green;">`Start`</mark>\
Обычно используется для настройки основных зависимостей (_если текущий скрипт использует другие компоненты_)

#### `Start`

Вызывается после загрузки сцены перед первым кадром\
Обычно используется для задания стартовых значений параметров либо же трансформации (_перемещение, вращение, масштаб_)

#### `Update`

Вызывается один раз за кадр до обновления кадра - **привязан к производительности игры**\
Обычно используется для системы ввода и проверки значений в других скриптах благодаря чему минимизируются задержки в работе игры

{% hint style="warning" %}
Не рекомендуется проводить дорогостоящие операции, такие как изменение физических параметров каждый кадр. Это оказывает значительное влияние на производительность
{% endhint %}

#### `FixedUpdate`

Вызывается каждый раз перед обновление физики - **почти не привязан к производительности** \
Рекомендуется перемещение и изменение физических свойств объекта переносить именно сюда для более корректно просчета

{% hint style="info" %}
В <mark style="color:green;">`FixedUpdate`</mark> умножать скорость на <mark style="color:green;">`Time.deltaTime`</mark> не требуется, т.к. время между обновлением физики почти одинаково
{% endhint %}

#### `LateUpdate`

Вызывается перед отрисовкой кадра, но после всех функций обновления (<mark style="color:green;">`Update`</mark><mark style="color:green;">,</mark> <mark style="color:green;"></mark><mark style="color:green;">`FixedUpdate`</mark>)

#### `OnEnable`

Вызывается при включении текущего компонента и при старте игры, если компонент в этот момент включен.

#### `OnDisable`

Вызывается при выключении текущего компонента, объекта, уничтожении объекта или удалении компонента с него.

### Постоянное вращение целей

Для создания нового скрипта нужно нажать ПКМ в окне <mark style="color:green;">Project -> Create -> C# Script</mark> и перетащите его на объект или же нажать <mark style="color:green;">Add Component</mark> на объекте, ввести его название и нажать <mark style="color:green;">New Script -> Create and Add.</mark>

![Новый скрипт на объекте (цель для игрока)](<.gitbook/assets/image (15).png>)

Чтобы открыть созданный скрипт можно просто дважды нажать на него.

По умолчанию он выглядит следующим образом:

```csharp
public class ConstantRotator : MonoBehaviour
{
    // Start is called before the first frame update
    void Start()
    {
        
    }

    // Update is called once per frame
    void Update()
    {
        
    }
}
```

Можно увидеть что был создал **C# класс**, который унаследован он <mark style="color:green;">`MonoBehaviout`</mark> <mark style="color:green;"></mark><mark style="color:green;"></mark> - позволяет использовать методы жизненного цикла и добавлять скрипт на объект.&#x20;

По умолчанию уже определено два метода жизненного цикла, которые являются приватными (`private`).

Теперь нужно реализовать постоянное вращение - бесконечно поворачивать объект на определенный угол.\
Во вращение и перемещении нам помогает свойство <mark style="color:green;">`transform`</mark>, которое если у любого <mark style="color:green;">`MonoBehaviout`</mark>, которое позволяет получить доступ к компоненту <mark style="color:green;">`Tranform`</mark>.\
Для вращения объекта используется метод <mark style="color:green;">`Rotate`</mark>, который принимает поворот в трех координатах - <mark style="color:green;">X, Y, Z</mark>. Просто добавим его в функцию <mark style="color:green;">`Update`</mark> и получим постоянное вращение.

```csharp
void Update()
    {
        transform.Rotate(0,0,5);
    }
```

### Вынос параметров скрипта в инспектор

Мы определи постоянное вращение в 5 градусов по оси Z, но что если геймдизайнер захочет изменить скорость или ось для вращения? Лезть в код и менять не вариант, ведь один и тот же скрипт может использоваться сразу на нескольких объектах

В Unity для скриптом можно указывать параметры, которые являются уникальными и способствуют повторному использованию уже написанных компонентов.\
Для этого в классе нужно определить **публичное поле...**

```csharp
public Vector3 RotationSpeed;
```

**...**и Unity автоматически отобразит его в <mark style="color:green;">Инспекторе</mark> на компоненте

![](<.gitbook/assets/image (27).png>)

Тип <mark style="color:green;">`Vector3`</mark> используется для задания значения по трем осям, каждое из которых представляет значение типа <mark style="color:green;">`float`</mark>.

Изменим код вращения, использовав поле <mark style="color:green;">`RotationSpeed`</mark>

```csharp
void Update()
{
    transform.Rotate(RotationSpeed);
}
```

Теперь у каждого объекта со скриптом <mark style="color:green;">`ConstantRotator`</mark> можно будет указать свою _уникальную_ скорость вращения.

### Трансформация объекта независимо от производительность

При постоянном изменении позиции или вращения объекта очень важно чтобы это происходило с одинаковой частотой, к примеру тут метод <mark style="color:green;">`Update`</mark> вызывается каждый кадр, из-за чего скорость вращения фактически привязана к производительности компьютера (_количеству кадров в секунду_) - чем больше кадров, тем быстрее вращается объект (_привет бегу в Fallout 76 или консольным играм заточенным под 30 FPS_).

Чтобы абстрагировать вращении или перемещение объекта от частоты кадров в секунду применяется несколько уловок:

#### `Time.deltaTime`

Изменять значения с той же частотой, но не на одинаковое значение, а привязать его в частоте кадров: при 60 вращать на 2.5 градуса, а при 30 на 5\
Чтобы это реализовать нужно умножать скорость на время, прошедшее с предыдущего кадра (фактически время между кадрами, которое напрямую зависит от частоты их обновления).\
<mark style="color:green;">`Time.deltaTime`</mark> - время, прошедшее с предыдущего вызова функции <mark style="color:green;">`Update`</mark>

```csharp
void Update()
{
    Vector3 fixedRotationSpeed = RotationSpeed * Time.deltaTime;
    transform.Rotate(fixedRotationSpeed);
}
```

#### `FixedUpdate`

Изменять значение с постоянной, фиксированной частотой - с помощью функции <mark style="color:green;">`FixedUpdate`</mark>.

```csharp
void FixedUpdate()
{
    transform.Rotate(RotationSpeed);
}
```

### Управление мячом

Создадим новый скрипт <mark style="color:green;">BallController</mark>, который будет отвечать за управление перемещением шара\
Чтобы проверить нажата ли определенная кнопка используется функция <mark style="color:green;">`Input.GetKey(KeyCode)`</mark> которая принимает код элемента и возвращает <mark style="color:green;">`true`</mark>, если она прямо сейчас нажата

```csharp
private void Update()
    {
        if (Input.GetKey(KeyCode.UpArrow)) 
        {
            //действие, если стрелка вверх нажата
        }
    }
```

Проверку пользовательского ввода мы вставили в функцию <mark style="color:green;">`Update`</mark>, т.к. хотим добиться максимальной отзывчивости

Теперь нам нужно реализовать перемещение шара вперед при нажатии стрелки вверх\
Для передвижения объекта используется метод <mark style="color:green;">`Translate`</mark> у объекта <mark style="color:green;">`tranform`</mark>, который принимает движение по трем координатам

```csharp
if (Input.GetKey(KeyCode.UpArrow))
{
    transform.Translate(0.1f, 0, 0);
}
```

Движение по вертикали будет изменять позицию по оси X, а по горизонтали - Z\
Скопируем код для остальных элементов управления

```csharp
float speed = 0.1f;
if (Input.GetKey(KeyCode.UpArrow))
{
 transform.Translate(speed, 0, 0);
}
if (Input.GetKey(KeyCode.DownArrow))
{
 transform.Translate(-speed, 0, 0);
}
if (Input.GetKey(KeyCode.LeftArrow))
{
 transform.Translate(0, 0, speed);
}
if (Input.GetKey(KeyCode.RightArrow))
{
 transform.Translate(0, 0, -speed);
}
```

Получилось очень много операторов `if`, а если учитывать что вызывать мы будем это каждый кадр могут образоваться еще и проверки с производительностью

Хорошо что в Unity уже есть инструмент для работы с осями ввода - <mark style="color:green;">`Input.GetAxis(axisName)`</mark>. Эта функция принимает название оси и возвращает дробное число от <mark style="color:green;">-1 до 1</mark>\
В качестве названия оси мы используем настроенные по умолчанию <mark style="color:green;">Horizontal</mark> и <mark style="color:green;">Vertical</mark> (<mark style="color:green;">ввод по вертикали и горизонтали соответственно</mark>)

```csharp
float horizontalInput = Input.GetAxis("Horizontal");
float verticalInput = Input.GetAxis("Vertical");
```

Таким образом мы сможем обрабатывать ввод не только с клавиатуры, но и с геймпада, т.к. оси ввода можно реализовать сразу для нескольких платформ

Теперь будем двигать шар по двум осям

```csharp
transform.Translate(verticalInput, 0, horizontalInput);
```

Однако теперь он двигается слишком быстро (если у вас много кадров в секунду) или наоборот. То есть его скорость привязана к количеству кадров\
Чтобы этого избежать умножим значения ввода на Time.deltaTime перед перемещением шара

```csharp
float fixedHorizontalInput = horizontalInput * Time.deltaTime;
float fixedVerticalInput = verticalInput * Time.deltaTime;
```

Теперь шар двигается корректно, но слишком медленно. Добавим поле <mark style="color:green;">`Speed`</mark> в наш скрипт, которое можно будет менять напрямую из <mark style="color:green;">Инспектора</mark> и умножим значения осей на скорость&#x20;

```csharp
public float Speed;
//...
float finalHorizontalOffset = fixedHorizontalInput * Speed;
float finalVerticalOffset = fixedVerticalInput * Speed;
```

В итоге скрипт выглядит следующим образом:

```csharp
public float Speed;
private void Update()
{
    float horizontalInput = Input.GetAxis("Horizontal");
    float verticalInput = Input.GetAxis("Vertical");
    float fixedHorizontalInput = horizontalInput * Time.deltaTime;
    float fixedVerticalInput = verticalInput * Time.deltaTime;
    float finalHorizontalOffset = fixedHorizontalInput * Speed;
    float finalVerticalOffset = fixedVerticalInput * Speed;
    transform.Translate(finalHorizontalOffset, 0, finalVerticalOffset);
}
```

### Триггеры

#### Создание триггера

Теперь нам нужно реализовать механику подбора (_уничтожения_) предмета при нахождении шара в коллайдере этого объекта

![](<.gitbook/assets/image (35).png>)

Возможность проверять находится ли коллайдер одного в другом предоставляет нам триггер.\
Для добавления триггера мы просто укажем галочку <mark style="color:green;">IsTrigger</mark> на компоненте <mark style="color:green;">Collider</mark> конкретного объекта

![](<.gitbook/assets/image (7).png>)

#### Функции взаимодействия с триггерами

* <mark style="color:green;">`OnTriggerEnter`</mark> - вызывается при входе в триггер
* <mark style="color:green;">`OnTriggerExit`</mark> - вызывается при выходе из триггера
* <mark style="color:green;">`OnTriggerStay`</mark> - вызывается в каждый момент нахождения объекта в триггере

Все эти функции принимают <mark style="color:green;">`Collider`</mark>, который и является триггером

#### Подбор предметов с помощью триггера

Теперь мы можем в скрипте шара проверить вошел ли его коллайдер в триггер.\
Создадим новый скрипт <mark style="color:green;">TriggerDestroyer</mark> и добавим в него системную функцию <mark style="color:green;">`OnTriggerEnter`</mark>

```csharp
private void OnTriggerEnter(Collider other)
{
    //действие при входе в триггер
}
```

Теперь нам нужно уничтожить объект, в триггер которого мы вошли. В Unity уже есть функция Destroy, которая принимает цель для уничтожения

```csharp
Destroy(other.gameObject);
```

В данном случае мы получаем игровой объект через компонент коллайдера

#### Теги

Но бывают ситуации когда нам нужно взаимодействовать не со всеми триггера, а только с конкретными. Для таких ситуаций существуют теги - специальные тестовые метки, которые может иметь любой объект.\
Изменим тег на нужный, если такого нет, то добавим его с помощью кнопки <mark style="color:green;">AddTag</mark>

![](<.gitbook/assets/image (23).png>)

![](<.gitbook/assets/image (4).png>)

Теперь добавим проверку на тег, вызвав у коллайдера функцию <mark style="color:green;">`CompareTag`</mark>, которая возвращает <mark style="color:green;">`true`</mark>, если на объекте он действительно есть

```csharp
if(other.CompareTag("Target"))
{
    //действие, если у объекта с триггером
    //"Target" установлен в качестве тега
}
```

Финальный код выглядит следующим образом:

```csharp
public class TriggerDestroyer : MonoBehaviour
{
    private void OnTriggerEnter(Collider other)
    {
        if(other.CompareTag("Target"))
        {
            Destroy(other.gameObject);
        }
    }
}
```

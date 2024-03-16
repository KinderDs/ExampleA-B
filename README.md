<div align='center'>
<h1>
 A/B тест!
  <img src="https://media.giphy.com/media/hvRJCLFzcasrR4ia7z/giphy.gif" width="30px"/>
</h1>
</div>
<div align='center'>
   <img src="https://img.shields.io/badge/Python-%23AFEEEE?style=for-the-badge&logo=Python&logoColor=yellow"/>
   <img src="https://img.shields.io/badge/pandas-%23AFEEEE?style=for-the-badge&logo=pandas&logoColor=white"/>
   <img src="https://img.shields.io/badge/scipy-%23AFEEEE?style=for-the-badge&logo=scipy&logoColor=white"/>
   <img src="https://img.shields.io/badge/Seaborn-%23AFEEEE?style=for-the-badge&logo=Seaborn"/>
   <img src="https://img.shields.io/badge/matplotlib-%23AFEEEE?style=for-the-badge&logo=matplotlib&logoColor=white"/>
   <img src="https://img.shields.io/badge/numpy%20-%23AFEEEE?style=for-the-badge&logo=numpy%20&logoColor=white"/>
   <img src="https://img.shields.io/badge/pingouin-%23AFEEEE?style=for-the-badge&logo=pingouin&logoColor=white"/>
</div>

 

## В ходе тестирования одной гипотезы целевой группе была предложена новая механика оплаты услуг на сайте, у контрольной группы оставалась базовая механика. Необходимо проанализировать итоги эксперимента и сделать вывод, стоит ли запускать новую механику оплаты на всех пользователей.

## Проведём разведочный анализ данных EDA.
В ходе анализа данных обнаружил, что в нашем общем датасете есть пользователи, которых система регистрирует как незаходящих на платформу (149 пользователей), НО! при этом фиксируется факт оплаты.
### Вывод:
Проанализоровав данные этих пользователей, выявил, что эти пользователи распределены не равномерно между группами, большинство (120) пользователей принадлежит целевой группе, а 29 пользователей контрольной. Так же суммы оплаты имеют разные значения - 13 уникальных значений.

   *   Система дала сбой и не зафиксировала факт посещения платформы.

   *   Транзакция была зафиксирована уже после введения новой фичи.

   *   Оплата с других ресурсов, либо автоматическое списание.

Не владеем полным спеком данных и возможности обговорить с заказчиком, считаю, что раз уж количество пользователей имеет большой перевес в сторону целевой группы - то это может повлиять на данные. Далее будем игнорировать эти данные.
### Пропущенные значения:
При проверки на пропущенные значения полного датасета, обнаружил пропуски (это связано с тем, что мы добавили доход с каждого пользователя, но многие не платили).
Заменим значения Nan в rev на нули и создадим булевую колонку (1 - была покупка, 0 - нет) для удобства расчётов.

## Далее ответим на следующие вопросы:

### На какие метрики обращать внимание?

В первую очередь в данном эксперименте нужно обратить внимание на Conversion Rate, так как она показывает сколько пользователей совершили конверсионное действие: тестируем новую механику оплаты - следовательно это факт оплаты.
Дополнительной метрикой буду рассматривать Average Order Value - средний чек.

### Имеются ли различия в показателях?
*   Конверсия в покупку между группами имеет небольшую разность.


<div align='centre'>
   <img src="https://github.com/KinderDs/ExampleA-B/assets/163444205/8bd1c433-4d25-4d3f-9842-e8b23230026d" width ="500" height="350">
</div>


*   По среднему чеку AOV можем сделать несколько выводов:

В обеих группах замечаны выбросы

Медианы имеют различие

AOV в группе B имеет больший межквартильный размах

Распределение является не нормальным

<div align='centre'>
   <img src="https://github.com/KinderDs/ExampleA-B/assets/163444205/4c03153b-80b5-43fc-a993-94fcfa780764" width ="800" height="350">
</div>

### Являются ли эти различия статистически значимыми?

   *   Определяем гипотезы для конверсии в покупку:

Нулевая гипотеза (H0): Разницы между конверсией в покупку в тестовой и контрольной группе нет.
Альтернативная гипотеза (H1): Разница между конверсией в покупку в тестовой и контрольной группе есть.  
P.S. Так как данные (purchase и grp) являются категориальными переменными, то будем использовать t-тест и тест Хи-квадрат!

![image](https://github.com/KinderDs/ExampleA-B/assets/163444205/018e1d1e-7840-459e-a70d-fb4d01c78ddd)
![image](https://github.com/KinderDs/ExampleA-B/assets/163444205/10184b1a-4431-4f47-af8b-00955daa085e)
   *   Вывод:

На боксплоте мы заметили небольшие различия между группами.Используя тест Хи-квадрат мы подтвердили, что оснований отклонить нулевую гипотезу (Разницы между конверсией в покупку в тестовой и контрольной группе нет) у нас нет.Наблюдаем низкие значения мощности ~ 11%. Данные низкие значения мощности говорят нам о том, что мы имеем высокие (89%) шансы столкнуться с ошибкой 2 рода. Иными словами: на 89% мы столкнулись с "Ложноотрицательным решением". На практике принято принимать значения мощности ~ 80%, что соответсвует 20 %-му шансу совершить ошибку 2 рода. Считаю, что мы имеем дело с "отложенным эффектом" и из-за недостаточности размера выборок мы ошибочно оставили нулевую гипотезу.

   *   Определяем гипотезы для среднего чека:

Нулевая гипотеза (H0):разницы между средними значениями среднего чека двух групп нет;
Альтернативная гипотеза (H1): разница между средними значениями есть

P.S. Анализируя сделаные выводы выше, приходим к выводу, что будем использовать бустрап для определения статистических различий.
![image](https://github.com/KinderDs/ExampleA-B/assets/163444205/4a550bda-2ceb-4693-a892-ff23af5f137e)

   *   Вывод:

Получили значения ср.чеков: группа А : 933.59 Группа B : 1257.88 - ср. чек тестовой группы значительно больше.Рассматривая график расределения AOV двух групп, мы наблюдаем значительные выбросы в группе В, подтверждаются они анализом количеством значений суммы покупки. Под вопрос на обсуждения попадают значения из тестовой группы (1900, 290, 1900.0001, 199). Данные значения очень похожи на какие-то ежемесячные/годовые подписки - возжно в этом и была фича новой системы оплаты. При использовании Вootstrap получили значения pvalue, которое не на много ниже 0.05 и 0 не входит в доверительный интервал.Это означет, что статистически мы подтвердили, что средний чек в обоих группах различается.

### Стоит ли запускать новую механику на всех пользователей?
Нужно поговорить с заказчиком и выяснить рост какой метрики его больше интересует.Если конверсия, то считаю нужно продолжить эксперимент, при данных выборках сложно делать какие-либо выводы и уж точно рано говорить о внедрении новой механики оплаты.Если средний чек, то данные эксперимента - подтверждают различая в группах и в тестовой группе со средним чеком лучше, следует можно вводить новую механику!

С заказчиком нужно обсудить несколько моментов: 

Мощность в анализе конверсии в покупку - необходимо определиться с каким порогом мощности он будет согласен (а точнее шансом совершить ошибку 2 рода) и продолжить эксперемент;

Обсудить возможные возникновения багов в системы - "Не заходили,Но! оплатили"; 

А так же обсудить обнаруженные значения "выбросы" из тестовой группы (1900, 290, 1900.0001, 199).

### P.S. Реализуем функцию, которая:

*   Автоматически подгружает информацию из дополнительного файла;
*   Пересчитывает метрики;
*   Строит графики по получаемым метрикам.

---

<details>
  <summary><b> 🛠 &nbsp;&nbsp;Используемые данные:&nbsp;</b></summary>
  <br/> 
   
*   groups.csv - файл с информацией о принадлежности пользователя к контрольной или экспериментальной группе (А – контроль, B – целевая группа)
   
*   groups_add.csv - дополнительный файл с пользователями, который прислали спустя 2 дня после передачи данных
  
*   active_studs.csv - файл с информацией о пользователях, которые зашли на платформу в дни проведения эксперимента.
  
*   checks.csv - файл с информацией об оплатах пользователей в дни проведения эксперимента.
  
</details>


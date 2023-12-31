# Использование Chrome DevTools - анализ открытия сайта.

### 1) Network 
**1.1) Профиль загрузки ресурсов при открытии страницы - [www.gd.ru.har](https://github.com/VictoriaSko/DevTools/blob/main/Network/www.gd.ru.har)**

**1.2) Неоптимальные места** <br />
1.2.1) Дублирование ресурсов
- www.1cont.ru
<img src="https://github.com/VictoriaSko/DevTools/blob/main/Network/Duplicate%201.png" data-canonical-src="https://github.com/VictoriaSko/DevTools/blob/main/Network/Duplicate%201.png"/>

- system_gd-logo.png
<img src="https://github.com/VictoriaSko/DevTools/blob/main/Network/Duplicate%202.png" data-canonical-src="https://github.com/VictoriaSko/DevTools/blob/main/Network/Duplicate%202.png"/>

- popper.min.js
<img src="https://github.com/VictoriaSko/DevTools/blob/main/Network/Duplicate%203.png" data-canonical-src="https://github.com/VictoriaSko/DevTools/blob/main/Network/Duplicate%203.png"/>

- jquery-3.5.1.js
<img src="https://github.com/VictoriaSko/DevTools/blob/main/Network/Duplicate%204.png" data-canonical-src="https://github.com/VictoriaSko/DevTools/blob/main/Network/Duplicate%204.png"/>

- fontawesome-webfont.woff2?v=4.7.0
<img src="https://github.com/VictoriaSko/DevTools/blob/main/Network/Duplicate%205.png" data-canonical-src="https://github.com/VictoriaSko/DevTools/blob/main/Network/Duplicate%205.png"/>

- data:image/png;base...
<img src="https://github.com/VictoriaSko/DevTools/blob/main/Network/Duplicate%206.png" data-canonical-src="https://github.com/VictoriaSko/DevTools/blob/main/Network/Duplicate%206.png"/>

- bootstrap.bundle.min.js, bootstrap.min.css, bootstrap.min.js
<img src="https://github.com/VictoriaSko/DevTools/blob/main/Network/Duplicate%207.png" data-canonical-src="https://github.com/VictoriaSko/DevTools/blob/main/Network/Duplicate%207.png"/>

- code.js
<img src="https://github.com/VictoriaSko/DevTools/blob/main/Network/Duplicate%208.png" data-canonical-src="https://github.com/VictoriaSko/DevTools/blob/main/Network/Duplicate%208.png"/>

- openapi.js
<img src="https://github.com/VictoriaSko/DevTools/blob/main/Network/Duplicate%209.png" data-canonical-src="https://github.com/VictoriaSko/DevTools/blob/main/Network/Duplicate%209.png"/>

- fontawesome-webfont.woff2?v=4.7.0
<img src="https://github.com/VictoriaSko/DevTools/blob/main/Network/Duplicate%2010.png" data-canonical-src="https://github.com/VictoriaSko/DevTools/blob/main/Network/Duplicate%2010.png"/>

1.2.2) Лишний размер ресурса <br />
Были выбраны запросы с размером > 140 kB при среднем размере ~30 kB
<img src="https://github.com/VictoriaSko/DevTools/blob/main/Network/Large.png" data-canonical-src="https://github.com/VictoriaSko/DevTools/blob/main/Network/Large.png"/>

При первичной загрузке страницы запрашивается JS скрипт yastatic.net/partner-code-bundles размером 120 kB, при это на момет загрузки страницы в нем используется менее 2% кода
<img src="https://github.com/VictoriaSko/DevTools/blob/main/Network/Large%201.1.png" data-canonical-src="https://github.com/VictoriaSko/DevTools/blob/main/Network/Large%201.1.png"/>
<img src="https://github.com/VictoriaSko/DevTools/blob/main/Network/Large%201.2.png" data-canonical-src="https://github.com/VictoriaSko/DevTools/blob/main/Network/Large%201.2.png"/>

При загрузке документа www.gd.ru осуществляется загрузка неиспользуемого кода JS и СSS в 41.6% от суммарного размера документа. Неиспользуемые сразу после загрузки скрипты и стили можно было бы загружать по мере необходимости
<img src="https://github.com/VictoriaSko/DevTools/blob/main/Network/Large%202.1.png" data-canonical-src="https://github.com/VictoriaSko/DevTools/blob/main/Network/Large%202.1.png"/>
<img src="https://github.com/VictoriaSko/DevTools/blob/main/Network/Large%202.2.png" data-canonical-src="https://github.com/VictoriaSko/DevTools/blob/main/Network/Large%202.2.png"/>

Также при входе на страницу загружаются стили common_frontend.css, среди которых сразу же используется менее 13% от общего объема файла
<img src="https://github.com/VictoriaSko/DevTools/blob/main/Network/Large%203.1.png" data-canonical-src="https://github.com/VictoriaSko/DevTools/blob/main/Network/Large%203.1.png"/>
<img src="https://github.com/VictoriaSko/DevTools/blob/main/Network/Large%203.2.png" data-canonical-src="https://github.com/VictoriaSko/DevTools/blob/main/Network/Large%203.2.png"/>

Кроме неиспользуемых сразу после загрузки скриптов и стилей, загружаются излишние размеры иконок, логотипов и изображений
<img src="https://github.com/VictoriaSko/DevTools/blob/main/Network/Large%204.png" data-canonical-src="https://github.com/VictoriaSko/DevTools/blob/main/Network/Large%204.png"/>
<img src="https://github.com/VictoriaSko/DevTools/blob/main/Network/Large%205.1.png" data-canonical-src="https://github.com/VictoriaSko/DevTools/blob/main/Network/Large%205.1.png"/>
<img src="https://github.com/VictoriaSko/DevTools/blob/main/Network/Large%205.2.png" data-canonical-src="https://github.com/VictoriaSko/DevTools/blob/main/Network/Large%205.2.png"/>

Кроме этого хотелось бы выделить изображение, которое является LCP - фоновая картинка черного цвета, которая имеет размер 4.1 kB
<img src="https://github.com/VictoriaSko/DevTools/blob/main/Network/Large%206.png" data-canonical-src="https://github.com/VictoriaSko/DevTools/blob/main/Network/Large%206.png"/>

1.2.3) Медленно загружающиеся ресурсы <br />
Были выбраны запросы длительностью >150ms
<img src="https://github.com/VictoriaSko/DevTools/blob/main/Network/Long%20Time.png" data-canonical-src="https://github.com/VictoriaSko/DevTools/blob/main/Network/Long%20Time.png"/>

1.2.4) Ресурсы, блокирующие загрузку <br />
Были выбраны запросы, начало которых произошло до этапа загрузки страницы First Paint
<img src="https://github.com/VictoriaSko/DevTools/blob/main/Network/Blocking%20Requests.png" data-canonical-src="https://github.com/VictoriaSko/DevTools/blob/main/Network/Blocking%20Requests.png"/>

1.2.5) Дополнительно выделенные запросы <br />
- Заблокированные запросы
<img src="https://github.com/VictoriaSko/DevTools/blob/main/Network/Blocked%20Requests.png" data-canonical-src="https://github.com/VictoriaSko/DevTools/blob/main/Network/Blocked%20Requests.png"/>

- Запросы, закончившиеся с ошибкой
<img src="https://github.com/VictoriaSko/DevTools/blob/main/Network/Failed%20Requests.png" data-canonical-src="https://github.com/VictoriaSko/DevTools/blob/main/Network/Failed%20Requests.png"/>

- Запросы со статусом 302, которые привели к лишним запросам по новым адресам
<img src="https://github.com/VictoriaSko/DevTools/blob/main/Network/302%20Status.png" data-canonical-src="https://github.com/VictoriaSko/DevTools/blob/main/Network/302%20Status.png"/>

- Запросы на загрузку изображений для кнопок, бейджиков и логотипов, которые могли бы быть реализованы в виде html элементов с css стилями, либо с добавлением изображений меньшего размера 
<img src="https://github.com/VictoriaSko/DevTools/blob/main/Network/Image%201.png" data-canonical-src="https://github.com/VictoriaSko/DevTools/blob/main/Network/Image%201.png"/>
<img src="https://github.com/VictoriaSko/DevTools/blob/main/Network/Image%202.png" data-canonical-src="https://github.com/VictoriaSko/DevTools/blob/main/Network/Image%202.png"/>

### 2) Performance
**2.1) Профиль загрузки страницы - [Trace.json](https://github.com/VictoriaSko/DevTools/blob/main/Performance/Trace.json)**

**2.2) Время в мс от начала навигации до событий:**
- **First Paint - 578.0 ms** <br />
<img src="https://github.com/VictoriaSko/DevTools/blob/main/Performance/First%20Paint.png" data-canonical-src="https://github.com/VictoriaSko/DevTools/blob/main/Performance/First%20Paint.png" width="200"/>

- **First Contentful Paint - 578.0 ms** <br />
<img src="https://github.com/VictoriaSko/DevTools/blob/main/Performance/First%20Contentful%20Paint.png" data-canonical-src="https://github.com/VictoriaSko/DevTools/blob/main/Performance/First%20Contentful%20Paint.png" width="200"/>

- **Largest Contentful Paint - 1055.0 ms** <br />
<img src="https://github.com/VictoriaSko/DevTools/blob/main/Performance/LCP.png" data-canonical-src="https://github.com/VictoriaSko/DevTools/blob/main/Performance/LCP.png" width="200"/>

- **DOMContentLoaded Event - 1006.2 ms** <br />
<img src="https://github.com/VictoriaSko/DevTools/blob/main/Performance/DOMContentLoaded%20Event.png" data-canonical-src="https://github.com/VictoriaSko/DevTools/blob/main/Performance/DOMContentLoaded%20Event.png" width="200"/>

- **Onload Event (Load) - 31215.9 ms** <br />
<img src="https://github.com/VictoriaSko/DevTools/blob/main/Performance/Onload%20Event.png" data-canonical-src="https://github.com/VictoriaSko/DevTools/blob/main/Performance/Onload%20Event.png" width="200"/>

**2.3) DOM-элемент, на котором происходит LCP** <br />
`<img loading="lazy" src="/images/branding/10/imageTop_1628667062.7856.jpg" data-url="/images/branding/10/imageTop_1628667062.7856.jpg" alt="-">`

<img src="https://github.com/VictoriaSko/DevTools/blob/main/Performance/LCP%20DOM%20Component.png" data-canonical-src="https://github.com/VictoriaSko/DevTools/blob/main/Performance/LCP%20DOM%20Component.png" width="500"/>

**2.4) Времz в миллисекундах, которое тратится на разные этапы обработки документа**
- **Loading - 21 ms** <br />
- **Scripting - 1583 ms** <br />
- **Rendering - 440 ms** <br />
- **Painting - 151 ms**

<img src="https://github.com/VictoriaSko/DevTools/blob/main/Performance/Page%20Loading.png" data-canonical-src="https://github.com/VictoriaSko/DevTools/blob/main/Performance/Page%20Loading.png" width="200"/>


### 3) Coverage
**3.1) Скриншот вкладки после загрузки страницы - [Coverage.png](https://github.com/VictoriaSko/DevTools/blob/main/Coverage/Coverage.png)**

**3.2) Объём неиспользованного CSS в ходе загрузки страницы в килобайтах** <br />
- **Unused CSS - 572 kB**
<img src="https://github.com/VictoriaSko/DevTools/blob/main/Coverage/Unused%20CSS.png" data-canonical-src="https://github.com/VictoriaSko/DevTools/blob/main/Coverage/Unused%20CSS.png" width="500"/>

**3.2) Объём неиспользованного JS в ходе загрузки страницы в килобайтах** <br />
- **Unused JS - 2764.8 kB**
<img src="https://github.com/VictoriaSko/DevTools/blob/main/Coverage/Unused%20JS.png" data-canonical-src="https://github.com/VictoriaSko/DevTools/blob/main/Coverage/Unused%20JS.png" width="500"/>

---

# Анализ открытия сайта при замедлении CPU 4x slowdown и эмуляцию сети Slow 3G.

### 1) Network 
**1.1) Профиль загрузки ресурсов при открытии страницы - [www.gd.ru-slow.har](https://github.com/VictoriaSko/DevTools/blob/main/Network/www.gd.ru-slow.har)**

**1.2) Неоптимальные места** <br />
1.2.1) Дублирование ресурсов <br />
Ресурсы аналогичны продублированным при обычной загрузке

1.2.2) Лишний размер ресурса <br />
Ресурсы аналогичны полученным при обычной загрузке

1.2.3) Медленно загружающиеся ресурсы <br />
Ресурсы аналогичны медленным при обычной загрузке

1.2.4) Ресурсы, блокирующие загрузку <br />
Ресурсы аналогичны блокирующим при обычной загрузке

1.2.5) Дополнительно выделенные запросы <br />
Ресурсы аналогичны выделенным при обычной загрузке

### 2) Performance
**2.1) Профиль загрузки страницы - [Trace-slow.json](https://github.com/VictoriaSko/DevTools/blob/main/Performance/Trace-slow.json.zip)**

**2.2) Время в мс от начала навигации до событий:**
- **First Paint - 9689.0 ms** <br />
<img src="https://github.com/VictoriaSko/DevTools/blob/main/Performance/First%20Paint%20Slow.png" data-canonical-src="https://github.com/VictoriaSko/DevTools/blob/main/Performance/First%20Paint%20Slow.png" width="200"/>

- **First Contentful Paint - 9689.4 ms** <br />
<img src="https://github.com/VictoriaSko/DevTools/blob/main/Performance/First%20Contentful%20Paint%20Slow.png" data-canonical-src="https://github.com/VictoriaSko/DevTools/blob/main/Performance/First%20Contentful%20Paint%20Slow.png" width="200"/>

- **Largest Contentful Paint - 33880.6 ms** <br />
<img src="https://github.com/VictoriaSko/DevTools/blob/main/Performance/LCP%20Slow.png" data-canonical-src="https://github.com/VictoriaSko/DevTools/blob/main/Performance/LCP%20Slow.png" width="200"/>

- **DOMContentLoaded Event - 29779.1 ms** <br />
<img src="https://github.com/VictoriaSko/DevTools/blob/main/Performance/DOMContentLoaded%20Event%20Slow.png" data-canonical-src="https://github.com/VictoriaSko/DevTools/blob/main/Performance/DOMContentLoaded%20Event%20Slow.png" width="200"/>

- **Onload Event (Load) - 53069.5 ms** <br />
<img src="https://github.com/VictoriaSko/DevTools/blob/main/Performance/Onload%20Event%20Slow.png" data-canonical-src="https://github.com/VictoriaSko/DevTools/blob/main/Performance/Onload%20Event%20Slow.png" width="200"/>

**2.3) DOM-элемент, на котором происходит LCP** <br />
`<img loading="lazy" src="/images/branding/10/imageTop_1628667062.7856.jpg" data-url="/images/branding/10/imageTop_1628667062.7856.jpg" alt="-">`

<img src="https://github.com/VictoriaSko/DevTools/blob/main/Performance/LCP%20DOM%20Component.png" data-canonical-src="https://github.com/VictoriaSko/DevTools/blob/main/Performance/LCP%20DOM%20Component.png" width="500"/>

**2.4) Время в миллисекундах, которое тратится на разные этапы обработки документа**
- **Loading - 90 ms** <br />
- **Scripting - 3467 ms** <br />
- **Rendering - 3788 ms** <br />
- **Painting - 1749 ms**

<img src="https://github.com/VictoriaSko/DevTools/blob/main/Performance/Page%20Loading%20Slow.png" data-canonical-src="https://github.com/VictoriaSko/DevTools/blob/main/Performance/Page%20Loading%20Slow.png" width="200"/>

### 3) Coverage
Данные не отличаются от полученных при анализе обычной загрузки страницы

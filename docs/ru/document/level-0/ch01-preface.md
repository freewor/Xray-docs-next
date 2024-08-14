# 【Глава 1】 Простыми словами

## 1.1 Для кого эта документация?

В двух словах: для **① новичков без опыта** **② желающих научиться настраивать свой собственный VPS**.

## 1.2 Для кого эта документация не предназначена?

В том числе, но не ограничиваясь: для всевозможных гуру и экспертов, для тех, кто слишком ленив, чтобы во всём разбираться самостоятельно, для тех, кто уже умеет настраивать VPS, для тех, кто точно решил пользоваться платными VPN-сервисами, для тех, кто предпочитает использовать готовые скрипты... Короче говоря, если у вас есть технические знания или вы не хотите настраивать всё сами, можете смело закрывать эту статью. Скорее всего, она покажется вам бесполезной и даже может вызвать раздражение, а оно вам надо?

## 1.3 Важное замечание и другие примечания

**Важное замечание:**

Я не являюсь техническим экспертом, поэтому в этой статье неизбежны пробелы и неточности. Если вы обнаружите какие-либо ошибки, пожалуйста, дайте мне знать об этом деликатно, без лишних эмоций.

**Отказ от ответственности:**

Пожалуйста, относитесь к информации, представленной в этой статье, критически и проверяйте её самостоятельно. Я не несу никакой ответственности за любые проблемы или негативные последствия, возникшие в результате использования информации из этой статьи.

**Предупреждение о многословности:**

Поскольку эта статья предназначена для **новичков без опыта**, многие вещи будут объяснены максимально подробно. Поэтому будьте готовы к тому, что текст будет довольно многословным.

## 1.4 Почему самостоятельная настройка  — это сложно?

Чтобы ответить на этот вопрос, нужно немного углубиться в историю вопроса.

Во-первых, обход блокировок существует уже почти двадцать лет (Шок! Ужас!). Сначала для этого достаточно было пары манипуляций (поправить файл hosts, подключиться по SSH), потом понадобились веб-прокси, затем — собственные протоколы (например, Shadowsocks) и так далее.

По мере того, как технологии блокировок совершенствовались на протяжении последних десятилетий, для самостоятельного обхода блокировок теперь нужно уметь:

- Разбираться в основных командах Linux.
- Понимать принципы работы сетевых протоколов.
- Иметь технические навыки и средства для покупки и управления VPS.
- Иметь технические навыки и средства для покупки и управления доменными именами.
- Уметь получать TLS-сертификаты.
- И многое другое.

Всё это превратило некогда простую задачу в пугающее испытание для новичков.

Во-вторых, о проблемах новичков.

Начинающим пользователям без технического бэкграунда, чтобы разобраться во всех этих премудростях, приходится изучать огромные массивы информации, разбросанной по всему интернету: блогам, форумам, группам в мессенджерах, репозиториям на GitHub, видео на YouTube и так далее. 

Вся эта информация часто оказывается противоречивой, неполной или попросту неверной. Новичкам остаётся только гадать, кому верить и как всё это работает на самом деле.

В итоге вместо нехватки информации новички сталкиваются с её избытком. После нескольких (скорее всего, неудачных) попыток разобраться во всём этом, их энтузиазм угасает. А если по пути им ещё и «посчастливится» обратиться за помощью не в то место, их могут ещё и высмеять: «Ну ты и нуб, проще уж платным VPN пользоваться, зачем изобретать велосипед?» или «Сначала Linux изучи, потом приходи».

В такие моменты остаётся только горько усмехнуться.

## 1.5 «Почему бы просто не пользоваться платным VPN?»

Во-первых, я хотел бы спросить у любителей подобных советов: разве платные VPN — это панацея?

Во-вторых, я считаю, что «не знать» и «не хотеть знать» — это две большие разницы. Конечно, инфантилы, которые хотят всё и сразу, не прилагая никаких усилий, вызывают только раздражение. Но люди, которые искренне хотят разобраться во всём сами, не заслуживают презрения и издёвок. Именно эта нетерпимость к новичкам и побудила меня написать эту статью. 

Давайте разберёмся, в чём плюсы и минусы платных VPN-сервисов.

**Плюсы:**

1. **Простота использования:** сканирование QR-кода, добавление правил в один клик и т.д.
2. **Большой выбор серверов:** доступ к ресурсам разных стран и регионов; например, выделенные серверы с низкой задержкой (iplc), серверы для онлайн-игр и т.д.
3. **Множество точек подключения:** выше устойчивость к блокировкам, если один сервер заблокируют, можно подключиться к другому.

**Риски:**

За удобство приходится платить, и в случае с платными VPN-сервисами риски следующие:

1. **VPN-провайдер имеет полный доступ к вашим данным:** всё, что вы делаете в интернете, **обязательно** проходит и **с большой вероятностью** хранится на серверах провайдера. Эти данные никак не защищены пользовательским соглашением или законом о защите персональных данных **(вас могут отслеживать и записывать всё, что вы делаете)**.
2. **Отсутствие регулирования рынка:** высока вероятность нарваться на мошенников **(провайдер может в любой момент исчезнуть с вашими деньгами)**.
3. **Давление со стороны регулирующих органов:** крупные VPN-провайдеры, с одной стороны, кажутся более надёжными, но, с другой стороны, чаще привлекают к себе внимание властей. В 2020 году было несколько случаев закрытия и прекращения работы крупных VPN-провайдеров, что привело к серьёзным неудобствам для пользователей **(провайдер может быть вынужден прекратить работу)**.
4. **Непрозрачность технических решений:** качество предоставляемых услуг может сильно варьироваться, не редки случаи обмана **(низкая скорость, частые обрывы связи, невозможность подключения)**.

## 1.6 Так стоит ли настраивать VPN самостоятельно?

Теперь, когда вы знаете о плюсах и минусах платных VPN, решать вам. В конце концов, лучший вариант — тот, который подходит именно вам.

![Выбор за вами!](./ch01-img01-choice.png)

1. Если вы решили воспользоваться платным VPN, можете закрыть эту статью.

2. Если же вы решили настроить всё самостоятельно, продолжайте чтение!

Цель этой статьи — стать отправной точкой для новичков, предоставить подробное пошаговое руководство по настройке VPN-сервера на VPS, начиная **с ввода первой команды** и заканчивая **успешным подключением к заблокированным ресурсам**. 

В процессе настройки вы познакомитесь с основными командами Linux, что станет хорошей базой для дальнейшего изучения этой операционной системы.

## 1.7 Немного лирики

1. В интернете много дезинформации, поэтому важно научиться критически мыслить, не поддаваться на провокации и не верить всему, что пишут.
2. Искренне надеюсь, что, получив доступ к свободному интернету, вы сможете узнавать больше нового, наслаждаться разнообразным контентом, знакомиться с интересными людьми и находить единомышленников. 
3. Ваша личность в интернете — это всё ещё вы. Добиться полной анонимности крайне сложно, поэтому не забывайте о законах вашей страны и стран, IP-адреса которых вы используете. Всегда помните о собственной безопасности.

## 1.8 Ваш прогресс

> ⬛⬜⬜⬜⬜⬜⬜⬜ 12.5%


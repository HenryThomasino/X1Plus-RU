# X1Plus
## Инструкции по установке
Добро пожаловать в X1Plus! Если вы пользователь, вы, вероятно, захотите сразу перейти на вики , где рассказывается все, что вам нужно знать об установке и использовании X1Plus на вашем принтере.

Остальная часть этого файла содержит скучные вещи для действительно больших ботаников, которые хотят разработать X1Plus.

## Инструкции по разработке
Хорошо, не говорите, что я вас не предупреждал. В любом случае, привет! Рад, что вы заинтересованы в участии в X1Plus! Вот куча информации о том, как его построить, как он структурирован внутри, а также различные вещи, которые вам, возможно, понадобится знать о том, как вносить изменения и как вносить свой вклад. X1Plus — результат года или около того нечетко структурированной работы; он начал свою жизнь как довольно грубый хак, и в течение последних нескольких месяцев мы усердно работали, пытаясь очистить его и выпустить во внешний мир. Тем не менее, некоторые детали все еще находятся в беспорядке, и нам очень жаль! Мы надеемся, что вы все равно поиграетесь с этим. Нам предстоит сделать много интересного, и мы пока лишь слегка коснулись поверхности.

## Как мне начать?
Вероятно, самый простой способ начать сборку X1Plus — использовать контейнер Docker. Если вы любите приключения, вы, вероятно, сможете собрать X1Plus на любой старой машине с Linux (я так и делаю), но если вы сделаете это, и он сломается, мы действительно не хотим об этом слышать, поэтому вам действительно следует просто собрать его в Docker. . Для сборки X1Plus вам понадобится ключ дешифрования файловой системы от работающего принтера (на котором работает X1Plus или официальная корневая прошивка); попробуйте что-то вроде:

<code>$ git clone ...
$ cd X1Plus
$ docker build -t x1plusbuild scripts/docker/
$ docker run -u `id -u` -v `pwd`:/work x1plusbuild bash -c 'git config --global --add safe.directory /work'
$ docker run -u `id -u` -v `pwd`:/work x1plusbuild make scripts
$ scp scripts/getkey root@bambu:/tmp
$ ssh root@bambu /tmp/getkey >> localconfig.mk
$ docker run -u `id -u` -v `pwd`:/work x1plusbuild make </code>

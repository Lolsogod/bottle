<script>
</script>

<h1>БУТЫЛОЧКА<sub>ДЛЯ ПАЦАНОВ</sub></h1>

<div id="titles">
  <div id="titlecontent">
    <p class="center">ЭПИЗОД V<br />НОВАЯ НАДЕЖДА ДЛЯ БОЛЬШОЙ КОМПАНИИ</p>

    <p>Давным давно в далеком далеком Саратове...</p>

    <p>
      Идет третий курс обучения в Политехничесском Государсвенном университете.
      Задают все более и более "сложные" задания. Но времени на их выполнение
      почти нет. Студенты придумывают новые идеи для реализации лабораторной
      работы.
    </p>

    <p>
      Толпы студентов усердно трудились, чтобы силой знаний выполнять свою
      работу. И все же тьма Темной Стороны Силы была сильна, и ученикам
      приходилось бороться с жестокими экзаменами с помощью своего ума и
      решимости.
    </p>

    <p>
      Но вот спасителем, джедаем в полноте своей надежды и веры стала защитница
      студентов: нейросеть ChatGPT. Теперь она ведет своих учеников в их борьбе
      против тирании темных профессоров и открывает им путь к победе и успеху.
    </p>

    <p>
      Так что присоединяйтесь к нам в этом эпическом путешествии, станьте
      свидетелем битв между силами знания и невежества и станьте частью нашей
      великой борьбы, ведь вместе мы учимся у силы в Саратовском государственном
      техническом университете!
    </p>

    <p>
      Для того чтобы удачно сдать предмет Стандартизация разработки программного
      обеспечения, группа студентов: Михаил, Кирилл и Саша Вожов сделали
      увлекательный эмулятор игры Бутылочка в стилистике Звёздные войны.
    </p>

    <p>
      Внутри пользователь сможет добавить игроков, а также задания, которые
      могут выпасть для выполения участникам игры. Но игроков не может быть
      больше 10.
    </p>

    <p>
      При создании рекомендуется не оставлять поля пустыми. Световой меч каждого
      игрока подсвечивается уникальным цветом для более явного обнаружения.
    </p>

    <p>Создатели заверяют в абсолютной случайности происходящий событий...</p>
  </div>
</div>

<style>
  @import url(https://fonts.googleapis.com/css?family=Droid+Sans:400,700);

  * {
    padding: 0;
    margin: 0;
  }

  body,
  html {
    width: 100%;
    height: 100%;
    font-family: "Droid Sans", arial, verdana, sans-serif;
    font-weight: 700;
    overflow: hidden;
  }

  @-webkit-keyframes intro {
    0% {
      opacity: 1;
    }
    90% {
      opacity: 1;
    }
    100% {
      opacity: 0;
    }
  }

  @-moz-keyframes intro {
    0% {
      opacity: 1;
    }
    90% {
      opacity: 1;
    }
    100% {
      opacity: 0;
    }
  }

  @-ms-keyframes intro {
    0% {
      opacity: 1;
    }
    90% {
      opacity: 1;
    }
    100% {
      opacity: 0;
    }
  }

  @-o-keyframes intro {
    0% {
      opacity: 1;
    }
    90% {
      opacity: 1;
    }
    100% {
      opacity: 0;
    }
  }

  @keyframes intro {
    0% {
      opacity: 1;
    }
    90% {
      opacity: 1;
    }
    100% {
      opacity: 0;
    }
  }

  h1 {
    position: absolute;
    width: fit-content;
    left: 50%;
    top: -50%;
    font-size: 10em;
    text-align: center;
    margin-left: -3em;
    line-height: 0.8em;
    letter-spacing: -0.05em;
    color: #000;
    text-shadow: -2px -2px 0 #ff6, 2px -2px 0 #ff6, -2px 2px 0 #ff6,
      2px 2px 0 #ff6;
    opacity: 0;
    z-index: 1;
    -webkit-animation: logo 5s ease-out 2.5s;
    -moz-animation: logo 5s ease-out 2.5s;
    -ms-animation: logo 5s ease-out 2.5s;
    -o-animation: logo 5s ease-out 2.5s;
    animation: logo 5s ease-out 2.5s;
  }

  h1 sub {
    display: block;
    font-size: 0.3em;
    letter-spacing: 0;
    line-height: 0.8em;
    width: 100%;
    text-align: center;
  }

  @-webkit-keyframes logo {
    0% {
      -webkit-transform: scale(1);
      opacity: 1;
    }
    50% {
      opacity: 1;
    }
    100% {
      -webkit-transform: scale(0.1);
      opacity: 0;
    }
  }

  @-moz-keyframes logo {
    0% {
      -moz-transform: scale(1);
      opacity: 1;
    }
    50% {
      opacity: 1;
    }
    100% {
      -moz-transform: scale(0.1);
      opacity: 0;
    }
  }

  @-ms-keyframes logo {
    0% {
      -ms-transform: scale(1);
      opacity: 1;
    }
    50% {
      opacity: 1;
    }
    100% {
      -ms-transform: scale(0.1);
      opacity: 0;
    }
  }

  @-o-keyframes logo {
    0% {
      -o-transform: scale(1);
      opacity: 1;
    }
    50% {
      opacity: 1;
    }
    100% {
      -o-transform: scale(0.1);
      opacity: 0;
    }
  }

  @keyframes logo {
    0% {
      transform: scale(1);
      opacity: 1;
    }
    50% {
      opacity: 1;
    }
    100% {
      transform: scale(0.1);
      opacity: 0;
    }
  }

  /* the interesting 3D scrolling stuff */
  #titles {
    color: #ff6;
    position: absolute;
    width: 28em;
    height: 50em;
    bottom: 0;
    left: 50%;
    margin-left: -14em;
    font-size: 350%;
    text-align: justify;
    overflow: hidden;
    -webkit-transform-origin: 50% 100%;
    -moz-transform-origin: 50% 100%;
    -ms-transform-origin: 50% 100%;
    -o-transform-origin: 50% 100%;
    transform-origin: 50% 100%;
    -webkit-transform: perspective(300px) rotateX(25deg);
    -moz-transform: perspective(300px) rotateX(25deg);
    -ms-transform: perspective(300px) rotateX(25deg);
    -o-transform: perspective(300px) rotateX(25deg);
    transform: perspective(700px) rotateX(25deg);
  }

  #titles p {
    text-align: justify;
    margin: 0.8em 0;
  }

  #titles p.center {
    text-align: center;
  }

  #titles a {
    color: #ff6;
    text-decoration: underline;
  }

  #titlecontent {
    position: absolute;
    top: 100%;
    -webkit-animation: scroll 100s linear 4s infinite;
    -moz-animation: scroll 100s linear 4s infinite;
    -ms-animation: scroll 100s linear 4s infinite;
    -o-animation: scroll 100s linear 4s infinite;
    animation: scroll 100s linear 4s infinite;
  }

  /* animation */
  @-webkit-keyframes scroll {
    0% {
      top: 100%;
    }
    100% {
      top: -170%;
    }
  }

  @-moz-keyframes scroll {
    0% {
      top: 100%;
    }
    100% {
      top: -170%;
    }
  }

  @-ms-keyframes scroll {
    0% {
      top: 100%;
    }
    100% {
      top: -170%;
    }
  }

  @-o-keyframes scroll {
    0% {
      top: 100%;
    }
    100% {
      top: -170%;
    }
  }

  @keyframes scroll {
    0% {
      top: 100%;
    }
    100% {
      top: -170%;
    }
  }
</style>

<!DOCTYPE html>
<html lang="ky">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">

    <title>Байэмир & Сезим — Үйлөнүү тою</title>

    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>

    <!-- Каллиграфиялык жана классикалык шрифттер -->
    <link href="https://fonts.googleapis.com/css2?family=Cormorant+Garamond:wght@400;500;600&family=Great+Vibes&display=swap" rel="stylesheet">

    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            background: #f7f5ef;
            color: #5b6045;
            font-family: "Cormorant Garamond", serif;
        }

        /* =========================
           COVER / CONVERТ
        ========================= */

        .cover {
            position: fixed;
            inset: 0;
            z-index: 100;
            background:
                radial-gradient(circle at center, #fffdf8 0%, #f2efe5 100%);
            display: flex;
            align-items: center;
            justify-content: center;
            transition: opacity 1.2s ease, visibility 1.2s ease;
        }

        .cover.hidden {
            opacity: 0;
            visibility: hidden;
            pointer-events: none;
        }

        .envelope {
            width: min(88vw, 430px);
            height: 280px;
            position: relative;
            cursor: pointer;
            filter: drop-shadow(0 18px 30px rgba(68, 70, 45, 0.15));
        }

        /* Конверттин негизги бөлүгү */
        .envelope-body {
            position: absolute;
            inset: 0;
            background: #fffdf8;
            border: 1px solid rgba(168, 137, 62, 0.35);
            overflow: hidden;
        }

        /* Сол жак бүктөм */
        .envelope-body::before {
            content: "";
            position: absolute;
            left: 0;
            bottom: 0;
            border-style: solid;
            border-width: 140px 210px 0 0;
            border-color: #eeeee3 transparent transparent transparent;
        }

        /* Оң жак бүктөм */
        .envelope-body::after {
            content: "";
            position: absolute;
            right: 0;
            bottom: 0;
            border-style: solid;
            border-width: 140px 0 0 210px;
            border-color: #e8e8dc transparent transparent transparent;
        }

        /* Үстүңкү клапан */
        .flap {
            position: absolute;
            top: 0;
            left: 0;
            width: 0;
            height: 0;
            border-left: 215px solid transparent;
            border-right: 215px solid transparent;
            border-top: 145px solid #f3f1e8;
            transform-origin: top;
            transition: transform 1.3s ease;
            z-index: 5;
        }

        .envelope.open .flap {
            transform: rotateX(180deg);
        }

        /* Алтын сызык */
        .gold-line {
            position: absolute;
            left: 7%;
            right: 7%;
            top: 7%;
            bottom: 7%;
            border: 1px solid rgba(169, 137, 61, 0.5);
            z-index: 6;
            pointer-events: none;
        }

        /* Текст */
        .invite-text {
            position: absolute;
            inset: 0;
            z-index: 7;
            display: flex;
            align-items: center;
            justify-content: center;
            flex-direction: column;
            pointer-events: none;
        }

        .invite-small {
            color: #a88b45;
            font-size: 12px;
            letter-spacing: 5px;
            text-transform: uppercase;
            margin-bottom: 8px;
        }

        .invite-title {
            font-family: "Great Vibes", cursive;
            font-size: 48px;
            color: #b0924d;
            line-height: 1;
        }

        .names-mini {
            margin-top: 12px;
            font-family: "Great Vibes", cursive;
            font-size: 22px;
            color: #697052;
        }

        .click-text {
            position: absolute;
            bottom: -48px;
            width: 100%;
            text-align: center;
            font-size: 14px;
            letter-spacing: 2px;
            color: #777b62;
            animation: pulse 2s infinite;
        }

        @keyframes pulse {
            0%, 100% {
                opacity: .45;
            }
            50% {
                opacity: 1;
            }
        }

        /* =========================
           MAIN CONTENT
        ========================= */

        .main {
            min-height: 100vh;
            background:
                linear-gradient(
                    rgba(250, 249, 244, .96),
                    rgba(246, 245, 237, .96)
                );
        }

        .hero {
            min-height: 100vh;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            text-align: center;
            padding: 50px 25px;
            position: relative;
            overflow: hidden;
        }

        .olive-decoration {
            position: absolute;
            width: 220px;
            height: 220px;
            border: 1px solid rgba(106, 112, 79, .15);
            border-radius: 50%;
        }

        .olive-decoration.one {
            top: -110px;
            left: -110px;
        }

        .olive-decoration.two {
            bottom: -110px;
            right: -110px;
        }

        .small-title {
            color: #a68a4b;
            font-size: 15px;
            letter-spacing: 5px;
            margin-bottom: 25px;
        }

        .hero h1 {
            font-family: "Great Vibes", cursive;
            font-size: clamp(62px, 15vw, 105px);
            font-weight: 400;
            color: #667052;
            line-height: .95;
        }

        .amp {
            color: #b0924d;
            font-size: .65em;
            margin: 0 8px;
        }

        .subtitle {
            margin-top: 28px;
            font-size: 18px;
            color: #70745e;
            letter-spacing: 2px;
        }

        .gold-divider {
            width: 100px;
            height: 1px;
            background: #b0924d;
            margin: 30px auto;
            position: relative;
        }

        .gold-divider::before,
        .gold-divider::after {
            content: "◆";
            position: absolute;
            top: -7px;
            color: #b0924d;
            font-size: 9px;
        }

        .gold-divider::before {
            left: -15px;
        }

        .gold-divider::after {
            right: -15px;
        }

        .invitation-text {
            max-width: 550px;
            font-size: 20px;
            line-height: 1.6;
            color: #646952;
        }

        /* =========================
           DETAILS
        ========================= */

        .details {
            padding: 80px 20px;
            background: #ececdf;
            text-align: center;
        }

        .section-title {
            font-family: "Great Vibes", cursive;
            font-size: 52px;
            color: #697052;
            font-weight: 400;
        }

        .detail-card {
            max-width: 550px;
            margin: 40px auto 0;
            padding: 45px 30px;
            background: rgba(255,255,255,.65);
            border: 1px solid rgba(168, 137, 62, .35);
        }

        .detail-item {
            margin: 25px 0;
        }

        .detail-label {
            color: #aa8b48;
            font-size: 13px;
            letter-spacing: 3px;
            text-transform: uppercase;
            margin-bottom: 7px;
        }

        .detail-value {
            color: #5e644b;
            font-size: 25px;
        }

        .restaurant {
            font-family: "Cormorant Garamond", serif;
            font-weight: 600;
            letter-spacing: 1px;
        }

        /* =========================
           FINAL
        ========================= */

        .final {
            min-height: 70vh;
            display: flex;
            align-items: center;
            justify-content: center;
            text-align: center;
            padding: 60px 25px;
        }

        .final-content {
            max-width: 600px;
        }

        .final p {
            font-size: 20px;
            line-height: 1.7;
            color: #666b54;
        }

        .final-names {
            font-family: "Great Vibes", cursive;
            font-size: 60px;
            color: #ad8f4c;
            margin-top: 30px;
        }

        footer {
            text-align: center;
            padding: 25px;
            font-size: 13px;
            letter-spacing: 2px;
            color: #858a70;
        }

        /* =========================
           MOBILE
        ========================= */

        @media (max-width: 500px) {

            .envelope {
                width: 88vw;
                height: 230px;
            }

            .flap {
                border-left-width: 44vw;
                border-right-width: 44vw;
                border-top-width: 120px;
            }

            .envelope-body::before {
                border-width: 115px 44vw 0 0;
            }

            .envelope-body::after {
                border-width: 115px 0 0 44vw;
            }

            .invite-title {
                font-size: 43px;
            }

            .invite-small {
                font-size: 10px;
                letter-spacing: 4px;
            }

            .hero {
                min-height: 100svh;
            }

            .hero h1 {
                font-size: 70px;
            }

            .invitation-text {
                font-size: 18px;
            }

            .section-title {
                font-size: 46px;
            }
        }
    </style>
</head>

<body>

    <!-- =========================
         БИРИНЧИ ЭКРАН — КОНВЕРТ
    ========================== -->

    <div class="cover" id="cover">

        <div class="envelope" id="envelope">

            <div class="envelope-body"></div>

            <div class="gold-line"></div>

            <div class="flap"></div>

            <div class="invite-text">
                <div class="invite-small">Үйлөнүү тоюна</div>

                <div class="invite-title">
                    Чакыруу
                </div>

                <div class="names-mini">
                    Байэмир & Сезим
                </div>
            </div>

            <div class="click-text">
                Конвертти ачыңыз
            </div>

        </div>

    </div>


    <!-- =========================
         НЕГИЗГИ САЙТ
    ========================== -->

    <main class="main" id="main">

        <section class="hero">

            <div class="olive-decoration one"></div>
            <div class="olive-decoration two"></div>

            <div class="small-title">
                ҮЙЛӨНҮҮ ТОЮ
            </div>

            <h1>
                Байэмир
                <span class="amp">&</span>
                Сезим
            </h1>

            <div class="gold-divider"></div>

            <p class="invitation-text">
                Сүйүүбүздүн эң бактылуу күнүндө
                сиздерди жаныбыздан көрүп,
                кубанычыбызды тең бөлүшүүгө чакырабыз.
            </p>

        </section>


        <!-- ТОЙДУН МААЛЫМАТТАРЫ -->

        <section class="details">

            <div class="section-title">
                Урматтуу коноктор!
            </div>

            <div class="detail-card">

                <div class="detail-item">
                    <div class="detail-label">
                        Дарек
                    </div>

                    <div class="detail-value">
                        Каракол шаары
                    </div>
                </div>


                <div class="detail-item">
                    <div class="detail-label">
                        Ресторан
                    </div>

                    <div class="detail-value restaurant">
                        «СОНО»
                    </div>
                </div>


                <div class="detail-item">
                    <div class="detail-label">
                        Башталышы
                    </div>

                    <div class="detail-value">
                        16:00
                    </div>
                </div>

            </div>

        </section>


        <!-- ЖЫЛУУ ТЕКСТ -->

        <section class="final">

            <div class="final-content">

                <div class="gold-divider"></div>

                <p>
                    Жакшылыгыбызга күбө болуп,
                    ак тилегиңиздерди айтып,
                    бактылуу күнүбүздүн көркүн ачып,
                    той төрүбүздүн сыйлуу коногу
                    болуп кетишиңиздерди каалайбыз.
                </p>

                <div class="final-names">
                    Байэмир & Сезим
                </div>

            </div>

        </section>


        <footer>
            СҮЙҮҮ МЕНЕН — БАЙЭМИР & СЕЗИМ
        </footer>

    </main>


    <script>

        const envelope = document.getElementById("envelope");
        const cover = document.getElementById("cover");

        envelope.addEventListener("click", function () {

            envelope.classList.add("open");

            setTimeout(() => {
                cover.classList.add("hidden");
                document.body.style.overflow = "auto";
            }, 1000);

        });

        document.body.style.overflow = "hidden";

    </script>

</body>
</html>

<!DOCTYPE html>
<html lang="ru">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width,initial-scale=1.0">

<title>MaxFlomShop</title>

<style>

*{
    box-sizing:border-box;
    margin:0;
    padding:0;
}

html{
    scroll-behavior:smooth;
}

body{
    min-height:100vh;
    font-family:Arial,sans-serif;
    color:#fff;
    background:
        radial-gradient(circle at 20% 20%,rgba(0,140,255,.28),transparent 35%),
        radial-gradient(circle at 80% 80%,rgba(0,70,255,.22),transparent 35%),
        linear-gradient(135deg,#020817,#031a3b,#00112c);
    overflow-x:hidden;
}

body::before{
    content:"";
    position:fixed;
    inset:0;
    pointer-events:none;
    background:
        radial-gradient(circle at 50% 0%,rgba(0,174,255,.14),transparent 35%);
    z-index:-1;
}

button,
input,
textarea{
    font:inherit;
}

button{
    cursor:pointer;
}

.hidden{
    display:none!important;
}

header{
    padding:25px 15px 10px;
    text-align:center;
}

.logo{
    font-size:clamp(40px,8vw,75px);
    font-weight:900;
    letter-spacing:3px;
    color:#fff;
    text-shadow:
        0 0 5px #00aaff,
        0 0 15px #00aaff,
        0 0 30px #0077ff,
        0 0 60px #0055ff;
    animation:neon 2s infinite alternate;
}

@keyframes neon{
    from{
        text-shadow:
        0 0 5px #00aaff,
        0 0 15px #00aaff,
        0 0 30px #0077ff;
    }

    to{
        text-shadow:
        0 0 8px #00ddff,
        0 0 25px #00aaff,
        0 0 50px #0066ff,
        0 0 80px #003cff;
    }
}

.subtitle{
    color:#9bdfff;
    margin-top:8px;
    font-size:15px;
}

.container{
    width:min(1150px,94%);
    margin:auto;
}

.topbar{
    margin:20px 0;
    padding:15px;
    border:1px solid rgba(0,174,255,.35);
    border-radius:18px;
    background:rgba(3,20,50,.75);
    backdrop-filter:blur(15px);
    box-shadow:0 0 30px rgba(0,119,255,.12);
    display:flex;
    gap:10px;
    justify-content:center;
    align-items:center;
    flex-wrap:wrap;
}

.user-info{
    padding:10px 15px;
    border-radius:12px;
    background:rgba(0,130,255,.12);
    border:1px solid rgba(0,170,255,.25);
}

.balance{
    color:#54dfff;
    font-weight:bold;
}

.btn{
    border:0;
    padding:11px 17px;
    border-radius:12px;
    color:#fff;
    background:linear-gradient(135deg,#0077ff,#00b7ff);
    box-shadow:0 0 15px rgba(0,145,255,.3);
    transition:.2s;
    font-weight:bold;
}

.btn:hover{
    transform:translateY(-2px) scale(1.02);
    box-shadow:0 0 25px rgba(0,180,255,.65);
}

.btn.red{
    background:linear-gradient(135deg,#d71945,#ff405f);
}

.btn.green{
    background:linear-gradient(135deg,#009d65,#00d98a);
}

.btn.dark{
    background:#10223e;
}

.btn.purple{
    background:linear-gradient(135deg,#6b19d9,#a63dff);
}

.btn.small{
    padding:8px 11px;
    font-size:13px;
}

.tabs{
    display:flex;
    justify-content:center;
    flex-wrap:wrap;
    gap:10px;
    margin:25px 0;
}

.tab{
    padding:12px 20px;
    border-radius:13px;
    border:1px solid rgba(0,180,255,.3);
    background:rgba(0,80,160,.15);
    color:#fff;
    transition:.2s;
}

.tab:hover,
.tab.active{
    background:linear-gradient(135deg,#0077ff,#00aaff);
    box-shadow:0 0 20px rgba(0,160,255,.5);
}

.products{
    display:grid;
    grid-template-columns:repeat(auto-fit,minmax(230px,1fr));
    gap:18px;
    margin-bottom:35px;
}

.product{
    padding:22px;
    min-height:210px;
    border-radius:20px;
    border:1px solid rgba(0,175,255,.28);
    background:
        linear-gradient(145deg,rgba(8,37,75,.9),rgba(2,15,35,.95));
    box-shadow:0 15px 40px rgba(0,0,0,.25);
    transition:.25s;
    display:flex;
    flex-direction:column;
}

.product:hover{
    transform:translateY(-6px);
    border-color:#00bfff;
    box-shadow:
        0 15px 45px rgba(0,100,255,.2),
        0 0 25px rgba(0,174,255,.15);
}

.product-icon{
    font-size:35px;
}

.product h3{
    margin:12px 0 8px;
}

.product p{
    color:#a8c9e9;
    font-size:14px;
    flex:1;
}

.price{
    font-size:23px;
    color:#53dcff;
    font-weight:bold;
    margin:16px 0;
}

.section{
    margin:25px 0;
    padding:22px;
    border-radius:20px;
    border:1px solid rgba(0,175,255,.25);
    background:rgba(2,19,43,.78);
    box-shadow:0 10px 35px rgba(0,0,0,.2);
}

.section h2{
    margin-bottom:15px;
}

.modal{
    position:fixed;
    inset:0;
    background:rgba(0,5,15,.78);
    backdrop-filter:blur(10px);
    z-index:1000;
    display:flex;
    justify-content:center;
    align-items:center;
    padding:15px;
}

.modal-box{
    width:min(560px,100%);
    max-height:90vh;
    overflow:auto;
    border-radius:22px;
    border:1px solid #009dff;
    background:linear-gradient(145deg,#061a35,#020b1c);
    box-shadow:0 0 50px rgba(0,120,255,.3);
    padding:25px;
}

.modal-box h2{
    margin-bottom:18px;
}

input,
textarea{
    width:100%;
    margin:7px 0;
    padding:13px;
    border-radius:11px;
    border:1px solid rgba(0,170,255,.35);
    outline:none;
    color:#fff;
    background:#071a32;
}

textarea{
    min-height:110px;
    resize:vertical;
}

input:focus,
textarea:focus{
    border-color:#00bfff;
    box-shadow:0 0 15px rgba(0,180,255,.15);
}

.form-buttons{
    display:flex;
    gap:10px;
    margin-top:12px;
    flex-wrap:wrap;
}

.payment-info{
    padding:16px;
    margin:15px 0;
    border-radius:15px;
    background:rgba(0,100,200,.12);
    border:1px solid rgba(0,175,255,.25);
}

.requisites{
    color:#55dcff;
    line-height:1.7;
}

.copy-number{
    display:flex;
    align-items:center;
    gap:8px;
    flex-wrap:wrap;
    margin-top:12px;
}

.number-box{
    flex:1;
    min-width:180px;
    padding:12px;
    border-radius:10px;
    background:#06172c;
    border:1px solid rgba(0,190,255,.3);
    color:#5edfff;
    font-weight:bold;
}

.order-code{
    margin:15px 0;
    padding:18px;
    border-radius:15px;
    border:1px solid #00c8ff;
    background:rgba(0,180,255,.08);
    text-align:center;
}

.order-code-title{
    color:#9bdfff;
    font-size:13px;
    margin-bottom:7px;
}

.order-code-value{
    font-size:27px;
    font-weight:900;
    color:#fff;
    letter-spacing:2px;
    text-shadow:0 0 15px #00bfff;
}

.notice{
    padding:13px;
    border-radius:12px;
    margin:10px 0;
    background:rgba(0,120,255,.1);
    border:1px solid rgba(0,160,255,.2);
}

.notice.error{
    border-color:#ff4766;
    background:rgba(255,40,80,.08);
}

.notice.success{
    border-color:#00d98a;
    background:rgba(0,220,130,.08);
}

.notice.warning{
    border-color:#ffbf40;
    background:rgba(255,180,0,.08);
}

.loading{
    text-align:center;
    padding:25px;
}

.spinner{
    width:45px;
    height:45px;
    margin:0 auto 15px;
    border:4px solid rgba(255,255,255,.15);
    border-top-color:#00bfff;
    border-radius:50%;
    animation:spin 1s linear infinite;
}

@keyframes spin{
    to{
        transform:rotate(360deg)
    }
}

.order{
    border:1px solid rgba(0,160,255,.22);
    border-radius:15px;
    margin:10px 0;
    overflow:hidden;
}

.order-head{
    padding:14px;
    background:rgba(0,100,190,.1);
    display:flex;
    justify-content:space-between;
    gap:10px;
    flex-wrap:wrap;
}

.order-body{
    padding:15px;
    line-height:1.7;
}

.status{
    padding:5px 9px;
    border-radius:8px;
    font-size:12px;
    display:inline-block;
}

.status.pending{
    background:#674900;
    color:#ffd96b;
}

.status.done{
    background:#005d43;
    color:#70ffc9;
}

.status.cancelled{
    background:#650019;
    color:#ff9aae;
}

.status.waiting{
    background:#173e67;
    color:#76d9ff;
}

.admin{
    border-color:#6d00ff;
    box-shadow:0 0 30px rgba(100,0,255,.12);
}

.admin-title{
    color:#c59cff;
}

.message{
    padding:14px;
    border-radius:12px;
    background:#081d38;
    margin:8px 0;
    border:1px solid rgba(0,160,255,.12);
}

.message.unread{
    border-left:3px solid #00c8ff;
}

.message.admin-message{
    border-left:3px solid #00d98a;
}

.support-user{
    padding:15px;
    margin:10px 0;
    border-radius:15px;
    background:#071a32;
    border:1px solid rgba(0,160,255,.25);
}

.support-user-head{
    display:flex;
    justify-content:space-between;
    gap:10px;
    flex-wrap:wrap;
    margin-bottom:10px;
}

.support-chat{
    margin-top:12px;
    padding-top:12px;
    border-top:1px solid rgba(255,255,255,.08);
}

.support-message{
    padding:10px;
    margin:7px 0;
    border-radius:10px;
    background:#0b2545;
}

.support-message.admin{
    background:rgba(0,210,130,.1);
    border-left:3px solid #00d98a;
}

.support-message.user{
    border-left:3px solid #00aaff;
}

.support-label{
    font-size:11px;
    color:#7fa4c7;
    margin-bottom:4px;
}

.empty{
    text-align:center;
    padding:25px;
    color:#7193b5;
}

footer{
    text-align:center;
    color:#6d8aaa;
    padding:30px 10px;
    font-size:13px;
}

@media(max-width:600px){

    .logo{
        font-size:42px;
    }

    .topbar{
        align-items:stretch;
    }

    .topbar>*{
        width:100%;
        text-align:center;
    }

    .products{
        grid-template-columns:1fr;
    }

    .copy-number{
        flex-direction:column;
    }

    .number-box{
        width:100%;
        text-align:center;
    }

}

</style>
</head>

<body>

<header>

    <div class="logo">
        MaxFlomShop
    </div>

    <div class="subtitle">
        Robux • Услуги • Аккаунты
    </div>

</header>


<div class="container">

    <!-- TOPBAR -->

    <div class="topbar">

        <div id="userBlock" class="user-info">
            Вы не авторизованы
        </div>

        <div id="balanceBlock" class="user-info hidden">

            Баланс:
            <span class="balance" id="balance">
                0 ₽
            </span>

        </div>

        <button
            class="btn"
            id="loginBtn"
            onclick="openAuth()">

            Войти

        </button>

        <button
            class="btn green hidden"
            id="depositBtn"
            onclick="openDeposit()">

            💳 Пополнить баланс

        </button>

        <button
            class="btn purple hidden"
            id="supportBtn"
            onclick="openSupport()">

            💬 Поддержка

        </button>

        <button
            class="btn dark hidden"
            id="messagesBtn"
            onclick="openMessages()">

            🔔 Сообщения

        </button>

        <button
            class="btn red hidden"
            id="logoutBtn"
            onclick="logout()">

            Выйти

        </button>

        <button
            class="btn hidden"
            id="adminBtn"
            onclick="openAdmin()">

            ⚙️ Админ-панель

        </button>

    </div>


    <div id="globalNotice"></div>


    <!-- CATEGORIES -->

    <div class="tabs">

        <button
            class="tab active"
            onclick="showCategory('robux',this)">

            💎 Робуксы

        </button>

        <button
            class="tab"
            onclick="showCategory('services',this)">

            🛠 Услуги

        </button>

        <button
            class="tab"
            onclick="showCategory('accounts',this)">

            👤 Аккаунты

        </button>

    </div>


    <div
        id="products"
        class="products">
    </div>

</div>


<footer>
    © 2026 MaxFlomShop
</footer>


<!-- AUTH -->

<div
    id="authModal"
    class="modal hidden">

    <div class="modal-box">

        <h2>
            🔐 Авторизация
        </h2>

        <div id="authNotice"></div>

        <input
            id="authEmail"
            type="email"
            placeholder="Email">

        <input
            id="authPassword"
            type="password"
            placeholder="Пароль">

        <div class="form-buttons">

            <button
                class="btn"
                onclick="login()">

                Войти

            </button>

            <button
                class="btn green"
                onclick="register()">

                Регистрация

            </button>

            <button
                class="btn dark"
                onclick="closeModal('authModal')">

                Закрыть

            </button>

        </div>

    </div>

</div>


<!-- BUY -->

<div
    id="buyModal"
    class="modal hidden">

    <div class="modal-box">

        <h2>
            🛒 Оформление заказа
        </h2>

        <div id="buyInfo"></div>

        <!-- ТОЛЬКО ДЛЯ ROBUX -->

        <div id="robloxNickBox">

            <input
                id="robloxNick"
                placeholder="Ваш Roblox ник">

            <div class="notice">
                🎮 Roblox ник нужен только при покупке Robux.
            </div>

        </div>


        <!-- ДЛЯ УСЛУГ И АККАУНТОВ -->

        <div
            id="serviceInstruction"
            class="hidden">

            <div class="notice warning">

                📱 После оплаты услуги или аккаунта
                напишите мне в личные сообщения.

                <br><br>

                Ваш код заказа:

                <b id="serviceOrderCodePreview">
                    —
                </b>

                <br><br>

                Укажите этот код в сообщении,
                чтобы я мог быстро найти ваш заказ.

            </div>

            <div class="copy-number">

                <div class="number-box">
                    79996512682
                </div>

                <button
                    class="btn"
                    onclick="copyPhone()">

                    📋 Скопировать номер

                </button>

            </div>

        </div>


        <div class="notice">

            После подтверждения заказ появится
            в системе администратора.

        </div>


        <div class="form-buttons">

            <button
                class="btn green"
                onclick="createOrder()">

                Подтвердить покупку

            </button>

            <button
                class="btn dark"
                onclick="closeModal('buyModal')">

                Отмена

            </button>

        </div>

    </div>

</div>


<!-- ORDER RESULT -->

<div
    id="orderResultModal"
    class="modal hidden">

    <div class="modal-box">

        <h2>
            ✅ Заказ создан
        </h2>

        <div class="notice success">

            Ваш заказ успешно создан.

        </div>

        <div class="order-code">

            <div class="order-code-title">
                КОД ЗАКАЗА
            </div>

            <div
                id="createdOrderCode"
                class="order-code-value">

                —

            </div>

        </div>

        <div id="createdOrderInstruction"></div>

        <div class="form-buttons">

            <button
                class="btn"
                onclick="copyCreatedOrderCode()">

                📋 Скопировать код

            </button>

            <button
                class="btn dark"
                onclick="closeModal('orderResultModal')">

                Закрыть

            </button>

        </div>

    </div>

</div>


<!-- DEPOSIT -->

<div
    id="depositModal"
    class="modal hidden">

    <div class="modal-box">

        <h2>
            💳 Пополнение баланса
        </h2>

        <div class="payment-info">

            <div class="requisites">

                <b>
                    Реквизиты для оплаты
                </b>

                <br><br>

                Сумма:

                <b>
                    <span id="depositAmountText">
                        0
                    </span>
                    ₽
                </b>

                <br>

                Номер / реквизиты:

                <b>
                    79996512682
                </b>

                <br>

                Банк:

                <b>
                    Т-Банк
                </b>

            </div>

        </div>


        <input
            id="depositAmount"
            type="number"
            min="1"
            placeholder="Введите сумму пополнения"
            oninput="updateDepositAmount()">


        <textarea
            id="depositComment"
            placeholder="Комментарий / дополнительные данные (необязательно)">
        </textarea>


        <div class="notice">

            📸 Фото чека прикреплять необязательно.

        </div>


        <div class="form-buttons">

            <button
                class="btn green"
                onclick="createDepositRequest()">

                Я перевёл деньги

            </button>

            <button
                class="btn dark"
                onclick="closeModal('depositModal')">

                Отмена

            </button>

        </div>

    </div>

</div>


<!-- SUPPORT -->

<div
    id="supportModal"
    class="modal hidden">

    <div class="modal-box">

        <h2>
            💬 Поддержка
        </h2>

        <div
            id="supportNotice">
        </div>

        <div
            id="supportHistory">

            <div class="empty">
                История поддержки пока не загружена.
            </div>

        </div>

        <textarea
            id="supportText"
            placeholder="Напишите свой вопрос...">
        </textarea>

        <div class="form-buttons">

            <button
                class="btn purple"
                onclick="sendSupportMessage()">

                📤 Отправить

            </button>

            <button
                class="btn dark"
                onclick="closeModal('supportModal')">

                Закрыть

            </button>

        </div>

    </div>

</div>


<!-- MESSAGES -->

<div
    id="messagesModal"
    class="modal hidden">

    <div class="modal-box">

        <h2>
            🔔 Мои сообщения
        </h2>

        <div id="messagesList"></div>

        <div class="form-buttons">

            <button
                class="btn dark"
                onclick="closeModal('messagesModal')">

                Закрыть

            </button>

        </div>

    </div>

</div>


<!-- ADMIN -->

<div
    id="adminModal"
    class="modal hidden">

    <div class="modal-box admin">

        <h2 class="admin-title">
            ⚙️ Админ-панель
        </h2>

        <div id="adminNotice"></div>


        <!-- USER -->

        <div class="section">

            <h2>
                👤 Покупатель
            </h2>

            <input
                id="adminUid"
                placeholder="Введите UID покупателя">

            <button
                class="btn"
                onclick="findUser()">

                Найти

            </button>

            <div id="userSearchResult"></div>

        </div>


        <!-- SEND MESSAGE -->

        <div class="section">

            <h2>
                💬 Отправить сообщение
            </h2>

            <input
                id="messageUid"
                placeholder="UID покупателя">

            <textarea
                id="messageText"
                placeholder="Введите сообщение">
            </textarea>

            <button
                class="btn"
                onclick="sendMessage()">

                📤 Отправить сообщение

            </button>

        </div>


        <!-- BALANCE -->

        <div class="section">

            <h2>
                💰 Выдать баланс
            </h2>

            <input
                id="balanceUid"
                placeholder="UID покупателя">

            <input
                id="balanceAmount"
                type="number"
                placeholder="Сумма ₽">

            <button
                class="btn green"
                onclick="addBalance()">

                Выдать баланс

            </button>

        </div>


        <!-- SUPPORT ADMIN -->

        <div class="section">

            <h2>
                💬 Поддержка
            </h2>

            <button
                class="btn dark"
                onclick="loadAdminSupport()">

                🔄 Обновить обращения

            </button>

            <div id="adminSupport"></div>

        </div>


        <!-- ORDERS -->

        <div class="section">

            <h2>
                📦 История заказов
            </h2>

            <button
                class="btn dark"
                onclick="loadAdminOrders()">

                🔄 Обновить историю

            </button>

            <div id="adminOrders"></div>

        </div>


        <!-- DEPOSITS -->

        <div class="section">

            <h2>
                💳 Заявки на пополнение
            </h2>

            <button
                class="btn dark"
                onclick="loadDeposits()">

                🔄 Обновить заявки

            </button>

            <div id="adminDeposits"></div>

        </div>


        <div class="form-buttons">

            <button
                class="btn dark"
                onclick="closeModal('adminModal')">

                Закрыть

            </button>

        </div>

    </div>

</div>


<script type="module">


/* =========================================================
   FIREBASE
========================================================= */

import {
    initializeApp
} from "https://www.gstatic.com/firebasejs/12.1.0/firebase-app.js";


import {
    getAuth,
    createUserWithEmailAndPassword,
    signInWithEmailAndPassword,
    signOut,
    onAuthStateChanged
} from "https://www.gstatic.com/firebasejs/12.1.0/firebase-auth.js";


import {
    getFirestore,
    doc,
    getDoc,
    setDoc,
    updateDoc,
    addDoc,
    collection,
    query,
    where,
    getDocs,
    serverTimestamp,
    limit
} from "https://www.gstatic.com/firebasejs/12.1.0/firebase-firestore.js";


const firebaseConfig = {

    apiKey:
        "AIzaSyA7hFpXtYghLXqipjaaQRItzmfDo_FHeq0",

    authDomain:
        "coffee-spark-ai-barista-344ce.firebaseapp.com",

    projectId:
        "coffee-spark-ai-barista-344ce",

    storageBucket:
        "coffee-spark-ai-barista-344ce.firebasestorage.app",

    messagingSenderId:
        "1064082579547",

    appId:
        "1:1064082579547:web:3d2d8bf5edb54b7f149f7e"

};


const app =
    initializeApp(firebaseConfig);


const auth =
    getAuth(app);


const db =
    getFirestore(app);


/* =========================================================
   ADMIN UID
========================================================= */

const ADMIN_UID =
    "uGqo5MfkbPg3aeeYkcW8KkYMqhq1";


/* =========================================================
   VARIABLES
========================================================= */

let currentUser = null;

let selectedProduct = null;

let currentCreatedOrderCode = "";


/* =========================================================
   PRODUCTS
========================================================= */

const products = {

    robux:[

        {
            id:"robux100",
            icon:"💎",
            name:"100 Робуксов",
            price:150,
            description:"100 Robux",
            category:"robux"
        },

        {
            id:"robux200",
            icon:"💎",
            name:"200 Робуксов",
            price:250,
            description:"200 Robux",
            category:"robux"
        },

        {
            id:"robux500",
            icon:"💎",
            name:"500 Робуксов",
            price:569,
            description:"500 Robux",
            category:"robux"
        },

        {
            id:"robux1000",
            icon:"💎",
            name:"1000 Робуксов",
            price:1210,
            description:"1000 Robux",
            category:"robux"
        },

        {
            id:"robux2000",
            icon:"💎",
            name:"2000 Робуксов",
            price:2199,
            description:"2000 Robux",
            category:"robux"
        }

    ],


    services:[

        {
            id:"cheats",
            icon:"🛠️",
            name:"Лучшие читы!",
            price:110,
            description:"Услуга",
            category:"services"
        },

        {
            id:"pr",
            icon:"📢",
            name:"Пиар",
            price:100,
            description:"Продвижение",
            category:"services"
        },

        {
            id:"uncheked",
            icon:"🎮",
            name:"Сделаю с Uncheked на обычный Roblox",
            price:50,
            description:"Услуга",
            category:"services"
        },

        {
            id:"steal",
            icon:"🚀",
            name:"Помогу развиться в Steal a agg",
            price:20,
            description:"Помощь",
            category:"services"
        },

        {
            id:"website",
            icon:"🌐",
            name:"Помогу создать сайт",
            price:1400,
            description:"Создание сайта",
            category:"services"
        }

    ],


    accounts:[

        {
            id:"account200",
            icon:"👤",
            name:"Донат 200 Robux",
            price:100,
            description:"Аккаунт",
            category:"accounts"
        },

        {
            id:"account1000",
            icon:"👤",
            name:"Донат 1000 Robux",
            price:699,
            description:"Аккаунт",
            category:"accounts"
        }

    ]

};


/* =========================================================
   SHOW PRODUCTS
========================================================= */

window.showCategory =
function(category,button){

    document
        .querySelectorAll(".tab")
        .forEach(x =>
            x.classList.remove("active")
        );


    if(button){

        button.classList.add("active");

    }


    const box =
        document.getElementById("products");


    box.innerHTML = "";


    products[category].forEach(product=>{

        const card =
            document.createElement("div");


        card.className =
            "product";


        card.innerHTML = `

            <div class="product-icon">
                ${product.icon}
            </div>

            <h3>
                ${escapeHtml(product.name)}
            </h3>

            <p>
                ${escapeHtml(product.description)}
            </p>

            <div class="price">
                ${product.price} ₽
            </div>

            <button
                class="btn"
                onclick='openBuy(${JSON.stringify(product)})'>

                Купить

            </button>

        `;


        box.appendChild(card);

    });

};


showCategory(
    "robux",
    document.querySelector(".tab")
);


/* =========================================================
   AUTH STATE
========================================================= */

onAuthStateChanged(
    auth,
    async(user)=>{

        currentUser =
            user;


        if(!user){

            document
                .getElementById("userBlock")
                .textContent =
                "Вы не авторизованы";


            document
                .getElementById("balanceBlock")
                .classList.add("hidden");


            document
                .getElementById("loginBtn")
                .classList.remove("hidden");


            document
                .getElementById("depositBtn")
                .classList.add("hidden");


            document
                .getElementById("supportBtn")
                .classList.add("hidden");


            document
                .getElementById("messagesBtn")
                .classList.add("hidden");


            document
                .getElementById("logoutBtn")
                .classList.add("hidden");


            document
                .getElementById("adminBtn")
                .classList.add("hidden");


            return;

        }


        document
            .getElementById("userBlock")
            .innerHTML =

            `👤 ${escapeHtml(
                user.email || "Пользователь"
            )}

            <br>

            <small>
                UID: ${escapeHtml(user.uid)}
            </small>`;


        document
            .getElementById("balanceBlock")
            .classList.remove("hidden");


        document
            .getElementById("loginBtn")
            .classList.add("hidden");


        document
            .getElementById("depositBtn")
            .classList.remove("hidden");


        document
            .getElementById("supportBtn")
            .classList.remove("hidden");


        document
            .getElementById("messagesBtn")
            .classList.remove("hidden");


        document
            .getElementById("logoutBtn")
            .classList.remove("hidden");


        if(user.uid === ADMIN_UID){

            document
                .getElementById("adminBtn")
                .classList.remove("hidden");

        }else{

            document
                .getElementById("adminBtn")
                .classList.add("hidden");

        }


        await loadBalance();

    }
);


/* =========================================================
   REGISTER
========================================================= */

window.register =
async function(){

    const email =
        document
            .getElementById("authEmail")
            .value
            .trim();


    const password =
        document
            .getElementById("authPassword")
            .value;


    if(!email || !password){

        authMessage(
            "Заполни email и пароль."
        );

        return;

    }


    if(password.length < 6){

        authMessage(
            "Пароль должен содержать минимум 6 символов."
        );

        return;

    }


    try{

        const result =
            await createUserWithEmailAndPassword(
                auth,
                email,
                password
            );


        await setDoc(
            doc(
                db,
                "users",
                result.user.uid
            ),
            {
                uid:
                    result.user.uid,

                email:
                    email,

                balance:
                    0,

                createdAt:
                    serverTimestamp()
            }
        );


        closeModal("authModal");


        notice(
            "Аккаунт успешно создан.",
            "success"
        );


    }catch(error){

        authMessage(
            firebaseError(error)
        );

    }

};


/* =========================================================
   LOGIN
========================================================= */

window.login =
async function(){

    const email =
        document
            .getElementById("authEmail")
            .value
            .trim();


    const password =
        document
            .getElementById("authPassword")
            .value;


    if(!email || !password){

        authMessage(
            "Введите email и пароль."
        );

        return;

    }


    try{

        await signInWithEmailAndPassword(
            auth,
            email,
            password
        );


        closeModal("authModal");


        notice(
            "Вы успешно вошли.",
            "success"
        );


    }catch(error){

        authMessage(
            firebaseError(error)
        );

    }

};


/* =========================================================
   LOGOUT
========================================================= */

window.logout =
async function(){

    await signOut(auth);

    notice(
        "Вы вышли из аккаунта."
    );

};


/* =========================================================
   BALANCE
========================================================= */

async function loadBalance(){

    if(!currentUser)
        return;


    try{

        const ref =
            doc(
                db,
                "users",
                currentUser.uid
            );


        const snap =
            await getDoc(ref);


        if(!snap.exists()){

            await setDoc(
                ref,
                {
                    uid:
                        currentUser.uid,

                    email:
                        currentUser.email || "",

                    balance:
                        0,

                    createdAt:
                        serverTimestamp()
                }
            );


            document
                .getElementById("balance")
                .textContent =
                "0 ₽";


            return;

        }


        const data =
            snap.data();


        document
            .getElementById("balance")
            .textContent =
            Number(data.balance || 0) + " ₽";


    }catch(error){

        notice(
            "Не удалось загрузить баланс.",
            "error"
        );

    }

}


/* =========================================================
   BUY
========================================================= */

window.openBuy =
function(product){

    if(!currentUser){

        openAuth();

        notice(
            "Сначала войдите в аккаунт."
        );

        return;

    }


    selectedProduct =
        product;


    document
        .getElementById("buyInfo")
        .innerHTML = `

            <div class="payment-info">

                <b>
                    ${escapeHtml(product.name)}
                </b>

                <br><br>

                Цена:

                <strong>
                    ${product.price} ₽
                </strong>

            </div>

        `;


    const nickBox =
        document.getElementById(
            "robloxNickBox"
        );


    const serviceInstruction =
        document.getElementById(
            "serviceInstruction"
        );


    if(product.category === "robux"){

        nickBox.classList.remove("hidden");

        serviceInstruction.classList.add("hidden");

        document
            .getElementById("robloxNick")
            .value = "";

    }else{

        nickBox.classList.add("hidden");

        serviceInstruction.classList.remove("hidden");

        const preview =
            generateOrderCode();


        document
            .getElementById(
                "serviceOrderCodePreview"
            )
            .textContent =
            preview;

        product.previewCode =
            preview;

    }


    openModal("buyModal");

};


/* =========================================================
   ORDER CODE
========================================================= */

function generateOrderCode(){

    const now =
        Date.now()
        .toString(36)
        .toUpperCase();


    const random =
        Math.random()
        .toString(36)
        .substring(2,7)
        .toUpperCase();


    return "MFS-" + now + "-" + random;

}


/* =========================================================
   CREATE ORDER
========================================================= */

window.createOrder =
async function(){

    if(!currentUser ||
       !selectedProduct){

        return;

    }


    let nick = "";


    if(
        selectedProduct.category ===
        "robux"
    ){

        nick =
            document
                .getElementById("robloxNick")
                .value
                .trim();


        if(!nick){

            notice(
                "Введите Roblox ник."
            );

            return;

        }

    }


    try{

        const userRef =
            doc(
                db,
                "users",
                currentUser.uid
            );


        const userSnap =
            await getDoc(userRef);


        if(!userSnap.exists()){

            notice(
                "Профиль пользователя не найден.",
                "error"
            );

            return;

        }


        const balance =
            Number(
                userSnap.data().balance || 0
            );


        if(
            balance <
            selectedProduct.price
        ){

            notice(
                `Недостаточно средств. Нужно ${selectedProduct.price} ₽.`,
                "error"
            );

            return;

        }


        const newBalance =
            balance -
            selectedProduct.price;


        await updateDoc(
            userRef,
            {
                balance:
                    newBalance
            }
        );


        const orderCode =
            selectedProduct.previewCode ||
            generateOrderCode();


        const orderRef =
            await addDoc(
                collection(
                    db,
                    "orders"
                ),
                {

                    userId:
                        currentUser.uid,

                    email:
                        currentUser.email || "",

                    productId:
                        selectedProduct.id,

                    productName:
                        selectedProduct.name,

                    price:
                        selectedProduct.price,

                    category:
                        selectedProduct.category,

                    robloxNick:
                        nick,

                    orderCode:
                        orderCode,

                    status:
                        "pending",

                    createdAt:
                        serverTimestamp()

                }
            );


        await addDoc(
            collection(
                db,
                "messages"
            ),
            {

                userId:
                    currentUser.uid,

                text:
                    `Ваш заказ «${selectedProduct.name}» принят. Код заказа: ${orderCode}.`,

                read:
                    false,

                fromAdmin:
                    false,

                createdAt:
                    serverTimestamp()

            }
        );


        closeModal("buyModal");


        await loadBalance();


        currentCreatedOrderCode =
            orderCode;


        document
            .getElementById(
                "createdOrderCode"
            )
            .textContent =
            orderCode;


        if(
            selectedProduct.category ===
            "robux"
        ){

            document
                .getElementById(
                    "createdOrderInstruction"
                )
                .innerHTML = `

                    <div class="notice">

                        🎮 Заказ на Robux создан.

                        <br><br>

                        Roblox ник:

                        <b>
                            ${escapeHtml(nick)}
                        </b>

                        <br><br>

                        Ожидайте выполнения заказа.

                    </div>

                `;

        }else{

            document
                .getElementById(
                    "createdOrderInstruction"
                )
                .innerHTML = `

                    <div class="notice warning">

                        📱 После оплаты напишите мне
                        в личные сообщения по номеру:

                        <br><br>

                        <b>
                            79996512682
                        </b>

                        <br><br>

                        И обязательно отправьте
                        <b>код заказа</b>:

                        <br>

                        <b>
                            ${escapeHtml(orderCode)}
                        </b>

                    </div>

                    <div class="copy-number">

                        <div class="number-box">
                            79996512682
                        </div>

                        <button
                            class="btn"
                            onclick="copyPhone()">

                            📋 Скопировать номер

                        </button>

                    </div>

                `;

        }


        openModal(
            "orderResultModal"
        );


        notice(
            "Заказ успешно создан.",
            "success"
        );


    }catch(error){

        notice(
            "Ошибка оформления заказа: " +
            firebaseError(error),
            "error"
        );

    }

};


/* =========================================================
   COPY PHONE
========================================================= */

window.copyPhone =
async function(){

    try{

        await navigator.clipboard.writeText(
            "79996512682"
        );


        notice(
            "Номер скопирован.",
            "success"
        );


    }catch(error){

        notice(
            "Не удалось скопировать номер."
        );

    }

};


/* =========================================================
   COPY ORDER CODE
========================================================= */

window.copyCreatedOrderCode =
async function(){

    if(!currentCreatedOrderCode)
        return;


    try{

        await navigator.clipboard.writeText(
            currentCreatedOrderCode
        );


        notice(
            "Код заказа скопирован.",
            "success"
        );


    }catch(error){

        notice(
            "Не удалось скопировать код."
        );

    }

};


/* =========================================================
   DEPOSIT
========================================================= */

window.openDeposit =
function(){

    if(!currentUser){

        openAuth();

        return;

    }


    document
        .getElementById(
            "depositAmount"
        )
        .value = "";


    document
        .getElementById(
            "depositComment"
        )
        .value = "";


    document
        .getElementById(
            "depositAmountText"
        )
        .textContent =
        "0";


    openModal(
        "depositModal"
    );

};


window.updateDepositAmount =
function(){

    const amount =
        Number(
            document
                .getElementById(
                    "depositAmount"
                )
                .value || 0
        );


    document
        .getElementById(
            "depositAmountText"
        )
        .textContent =
        amount > 0
        ? amount
        : 0;

};


window.createDepositRequest =
async function(){

    if(!currentUser)
        return;


    const amount =
        Number(
            document
                .getElementById(
                    "depositAmount"
                )
                .value
        );


    const comment =
        document
            .getElementById(
                "depositComment"
            )
            .value
            .trim();


    if(!amount || amount <= 0){

        notice(
            "Введите сумму пополнения."
        );

        return;

    }


    try{

        await addDoc(
            collection(
                db,
                "depositRequests"
            ),
            {

                userId:
                    currentUser.uid,

                email:
                    currentUser.email || "",

                amount:
                    amount,

                comment:
                    comment,

                status:
                    "pending",

                hasPhoto:
                    false,

                createdAt:
                    serverTimestamp()

            }
        );


        closeModal(
            "depositModal"
        );


        notice(
            "Заявка на пополнение отправлена администратору.",
            "success"
        );


    }catch(error){

        notice(
            "Ошибка создания заявки: " +
            firebaseError(error),
            "error"
        );

    }

};


/* =========================================================
   USER SUPPORT
========================================================= */

window.openSupport =
async function(){

    if(!currentUser){

        openAuth();

        notice(
            "Сначала войдите в аккаунт."
        );

        return;

    }


    openModal(
        "supportModal"
    );


    await loadSupportHistory();

};


async function loadSupportHistory(){

    const box =
        document.getElementById(
            "supportHistory"
        );


    box.innerHTML =
        `

        <div class="loading">

            <div class="spinner"></div>

            Загрузка поддержки...

        </div>

        `;


    try{

        const q =
            query(
                collection(
                    db,
                    "supportMessages"
                ),
                where(
                    "userId",
                    "==",
                    currentUser.uid
                ),
                limit(100)
            );


        const snap =
            await getDocs(q);


        if(snap.empty){

            box.innerHTML =
                `

                <div class="empty">

                    Напишите свой вопрос.
                    Администратор ответит здесь.

                </div>

                `;

            return;

        }


        const messages = [];


        snap.forEach(item=>{

            const data =
                item.data();


            messages.push({
                id:item.id,
                ...data
            });

        });


        messages.sort(
            (a,b)=>
                getTimestamp(a.createdAt) -
                getTimestamp(b.createdAt)
        );


        box.innerHTML = "";


        messages.forEach(data=>{

            const div =
                document.createElement("div");


            div.className =
                "support-message " +
                (
                    data.fromAdmin
                    ? "admin"
                    : "user"
                );


            div.innerHTML = `

                <div class="support-label">

                    ${
                        data.fromAdmin
                        ? "👨‍💼 Администратор"
                        : "👤 Вы"
                    }

                </div>

                ${escapeHtml(
                    data.text || ""
                )}

            `;


            box.appendChild(div);

        });


    }catch(error){

        box.innerHTML =
            `

            <div class="notice error">

                Не удалось загрузить поддержку.

                <br><br>

                ${escapeHtml(
                    firebaseError(error)
                )}

            </div>

            `;

    }

}


/* =========================================================
   SEND SUPPORT MESSAGE
========================================================= */

window.sendSupportMessage =
async function(){

    if(!currentUser)
        return;


    const text =
        document
            .getElementById(
                "supportText"
            )
            .value
            .trim();


    if(!text){

        document
            .getElementById(
                "supportNotice"
            )
            .innerHTML =
            `

            <div class="notice error">

                Напишите сообщение.

            </div>

            `;

        return;

    }


    try{

        await addDoc(
            collection(
                db,
                "supportMessages"
            ),
            {

                userId:
                    currentUser.uid,

                email:
                    currentUser.email || "",

                text:
                    text,

                fromAdmin:
                    false,

                read:
                    false,

                createdAt:
                    serverTimestamp()

            }
        );


        document
            .getElementById(
                "supportText"
            )
            .value = "";


        document
            .getElementById(
                "supportNotice"
            )
            .innerHTML =
            `

            <div class="notice success">

                Сообщение отправлено.
                Ожидайте ответа администратора.

            </div>

            `;


        await loadSupportHistory();


    }catch(error){

        document
            .getElementById(
                "supportNotice"
            )
            .innerHTML =
            `

            <div class="notice error">

                Ошибка отправки:
                ${escapeHtml(
                    firebaseError(error)
                )}

            </div>

            `;

    }

};


/* =========================================================
   USER MESSAGES
========================================================= */

window.openMessages =
async function(){

    if(!currentUser){

        openAuth();

        return;

    }


    openModal(
        "messagesModal"
    );


    const list =
        document.getElementById(
            "messagesList"
        );


    list.innerHTML =
        `

        <div class="loading">

            <div class="spinner"></div>

            Загрузка...

        </div>

        `;


    try{

        /*
        ВАЖНО:
        Здесь специально НЕТ orderBy().
        Поэтому сообщения не требуют
        дополнительного Firestore index.
        */

        const q =
            query(
                collection(
                    db,
                    "messages"
                ),
                where(
                    "userId",
                    "==",
                    currentUser.uid
                ),
                limit(100)
            );


        const snap =
            await getDocs(q);


        if(snap.empty){

            list.innerHTML =
                `

                <div class="empty">

                    Сообщений пока нет.

                </div>

                `;

            return;

        }


        const messages = [];


        snap.forEach(item=>{

            const data =
                item.data();


            messages.push({
                id:item.id,
                ...data
            });

        });


        messages.sort(
            (a,b)=>
                getTimestamp(b.createdAt) -
                getTimestamp(a.createdAt)
        );


        list.innerHTML = "";


        messages.forEach(data=>{

            const div =
                document.createElement(
                    "div"
                );


            div.className =
                "message " +
                (
                    data.read
                    ? ""
                    : "unread"
                ) +
                (
                    data.fromAdmin
                    ? " admin-message"
                    : ""
                );


            div.innerHTML = `

                <b>

                    ${
                        data.fromAdmin
                        ? "👨‍💼 Администратор"
                        : "🔔 Уведомление"
                    }

                </b>

                <br><br>

                ${escapeHtml(
                    data.text || ""
                )}

            `;


            list.appendChild(div);

        });


    }catch(error){

        list.innerHTML =
            `

            <div class="notice error">

                Не удалось загрузить сообщения.

                <br><br>

                ${escapeHtml(
                    firebaseError(error)
                )}

            </div>

            `;

    }

};


/* =========================================================
   ADMIN CHECK
========================================================= */

function checkAdmin(){

    if(!currentUser){

        return false;

    }


    if(
        currentUser.uid !==
        ADMIN_UID
    ){

        notice(
            "Доступ запрещён.",
            "error"
        );

        return false;

    }


    return true;

}


/* =========================================================
   OPEN ADMIN
========================================================= */

window.openAdmin =
async function(){

    if(!checkAdmin())
        return;


    openModal(
        "adminModal"
    );


    await loadAdminOrders();

    await loadDeposits();

    await loadAdminSupport();

};


/* =========================================================
   FIND USER
========================================================= */

window.findUser =
async function(){

    if(!checkAdmin())
        return;


    const uid =
        document
            .getElementById(
                "adminUid"
            )
            .value
            .trim();


    if(!uid){

        adminNotice(
            "Введите UID.",
            "error"
        );

        return;

    }


    const box =
        document.getElementById(
            "userSearchResult"
        );


    try{

        const snap =
            await getDoc(
                doc(
                    db,
                    "users",
                    uid
                )
            );


        if(!snap.exists()){

            box.innerHTML =
                `

                <div class="notice error">

                    Пользователь не найден.

                </div>

                `;

            return;

        }


        const data =
            snap.data();


        box.innerHTML =
            `

            <div class="notice success">

                <b>
                    Пользователь найден
                </b>

                <br><br>

                UID:
                ${escapeHtml(uid)}

                <br>

                Email:
                ${escapeHtml(
                    data.email || ""
                )}

                <br>

                Баланс:
                ${Number(
                    data.balance || 0
                )} ₽

            </div>

            `;


    }catch(error){

        box.innerHTML =
            `

            <div class="notice error">

                Ошибка поиска.

            </div>

            `;

    }

};


/* =========================================================
   ADMIN SEND MESSAGE
========================================================= */

window.sendMessage =
async function(){

    if(!checkAdmin())
        return;


    const uid =
        document
            .getElementById(
                "messageUid"
            )
            .value
            .trim();


    const text =
        document
            .getElementById(
                "messageText"
            )
            .value
            .trim();


    if(!uid || !text){

        adminNotice(
            "Заполни UID и сообщение.",
            "error"
        );

        return;

    }


    try{

        const user =
            await getDoc(
                doc(
                    db,
                    "users",
                    uid
                )
            );


        if(!user.exists()){

            adminNotice(
                "Такого пользователя нет.",
                "error"
            );

            return;

        }


        await addDoc(
            collection(
                db,
                "messages"
            ),
            {

                userId:
                    uid,

                text:
                    text,

                read:
                    false,

                createdAt:
                    serverTimestamp(),

                fromAdmin:
                    true

            }
        );


        document
            .getElementById(
                "messageText"
            )
            .value = "";


        adminNotice(
            "Сообщение отправлено. Оно появится у покупателя во вкладке «Сообщения».",
            "success"
        );


    }catch(error){

        adminNotice(
            "Ошибка отправки сообщения: " +
            firebaseError(error),
            "error"
        );

    }

};


/* =========================================================
   ADD BALANCE
========================================================= */

window.addBalance =
async function(){

    if(!checkAdmin())
        return;


    const uid =
        document
            .getElementById(
                "balanceUid"
            )
            .value
            .trim();


    const amount =
        Number(
            document
                .getElementById(
                    "balanceAmount"
                )
                .value
        );


    if(
        !uid ||
        !amount ||
        amount <= 0
    ){

        adminNotice(
            "Введите UID и положительную сумму.",
            "error"
        );

        return;

    }


    try{

        const ref =
            doc(
                db,
                "users",
                uid
            );


        const snap =
            await getDoc(ref);


        if(!snap.exists()){

            adminNotice(
                "Пользователь не найден.",
                "error"
            );

            return;

        }


        const currentBalance =
            Number(
                snap.data().balance || 0
            );


        await updateDoc(
            ref,
            {
                balance:
                    currentBalance +
                    amount
            }
        );


        await addDoc(
            collection(
                db,
                "messages"
            ),
            {

                userId:
                    uid,

                text:
                    `Администратор пополнил ваш баланс на ${amount} ₽.`,

                read:
                    false,

                createdAt:
                    serverTimestamp(),

                fromAdmin:
                    true

            }
        );


        adminNotice(
            `Баланс увеличен на ${amount} ₽.`,
            "success"
        );


    }catch(error){

        adminNotice(
            "Ошибка изменения баланса.",
            "error"
        );

    }

};


/* =========================================================
   ADMIN ORDERS
========================================================= */

window.loadAdminOrders =
async function(){

    if(!checkAdmin())
        return;


    const box =
        document.getElementById(
            "adminOrders"
        );


    box.innerHTML =
        `

        <div class="loading">

            <div class="spinner"></div>

            Загрузка заказов...

        </div>

        `;


    try{

        /*
        НЕТ orderBy().
        Это исправляет проблему
        с отсутствующим Firestore index.
        */

        const q =
            query(
                collection(
                    db,
                    "orders"
                ),
                limit(100)
            );


        const snap =
            await getDocs(q);


        if(snap.empty){

            box.innerHTML =
                `

                <div class="empty">

                    Заказов нет.

                </div>

                `;

            return;

        }


        const orders = [];


        snap.forEach(item=>{

            orders.push({
                id:item.id,
                ...item.data()
            });

        });


        orders.sort(
            (a,b)=>
                getTimestamp(b.createdAt) -
                getTimestamp(a.createdAt)
        );


        box.innerHTML = "";


        orders.forEach(data=>{

            const order =
                document.createElement(
                    "div"
                );


            order.className =
                "order";


            const statusClass =
                data.status === "done"
                ? "done"
                : data.status === "cancelled"
                ? "cancelled"
                : "pending";


            const statusText =
                data.status === "done"
                ? "Выполнен"
                : data.status === "cancelled"
                ? "Отменён"
                : "В обработке";


            const nickLine =
                data.category === "robux"
                ? `

                    <br>

                    Roblox ник:
                    <b>
                        ${escapeHtml(
                            data.robloxNick || ""
                        )}
                    </b>

                  `
                : "";


            const contactLine =
                data.category !== "robux"
                ? `

                    <br>

                    📱 Покупателю нужно
                    написать:

                    <b>
                        79996512682
                    </b>

                  `
                : "";


            order.innerHTML = `

                <div class="order-head">

                    <div>

                        <b>
                            ${escapeHtml(
                                data.productName || ""
                            )}
                        </b>

                        <br>

                        <small>

                            UID:
                            ${escapeHtml(
                                data.userId || ""
                            )}

                        </small>

                    </div>


                    <div>

                        <span
                            class="status ${statusClass}">

                            ${statusText}

                        </span>


                        <button
                            class="btn small dark"
                            onclick="toggleOrder('${data.id}')">

                            Развернуть

                        </button>

                    </div>

                </div>


                <div
                    id="order-${data.id}"
                    class="order-body hidden">

                    Цена:

                    <b>
                        ${Number(
                            data.price || 0
                        )} ₽
                    </b>

                    <br>

                    Код заказа:

                    <b>
                        ${escapeHtml(
                            data.orderCode || "—"
                        )}
                    </b>

                    ${nickLine}

                    ${contactLine}

                    <br>

                    Email:

                    ${escapeHtml(
                        data.email || ""
                    )}

                    <br>

                    UID:

                    ${escapeHtml(
                        data.userId || ""
                    )}

                    <br><br>


                    <button
                        class="btn green"
                        onclick="completeOrder('${data.id}','${data.userId}')"
                        ${data.status === "done" ? "disabled" : ""}>

                        ${
                            data.status === "done"
                            ? "✓ Уже выполнен"
                            : "✓ Заказ выполнен"
                        }

                    </button>


                    <button
                        class="btn red"
                        onclick="cancelOrder('${data.id}','${data.userId}')"
                        ${data.status === "cancelled" ? "disabled" : ""}>

                        ✕ Отменить

                    </button>

                </div>

            `;


            box.appendChild(order);

        });


    }catch(error){

        box.innerHTML =
            `

            <div class="notice error">

                Не удалось загрузить историю.

                <br><br>

                ${escapeHtml(
                    firebaseError(error)
                )}

            </div>

            `;

    }

};


/* =========================================================
   TOGGLE ORDER
========================================================= */

window.toggleOrder =
function(id){

    const el =
        document.getElementById(
            "order-" + id
        );


    if(!el)
        return;


    el.classList.toggle(
        "hidden"
    );

};


/* =========================================================
   COMPLETE ORDER
========================================================= */

window.completeOrder =
async function(
    orderId,
    userId
){

    if(!checkAdmin())
        return;


    try{

        await updateDoc(
            doc(
                db,
                "orders",
                orderId
            ),
            {

                status:
                    "done",

                completedAt:
                    serverTimestamp()

            }
        );


        await addDoc(
            collection(
                db,
                "messages"
            ),
            {

                userId:
                    userId,

                text:
                    "✅ Ваш заказ выполнен! Спасибо за покупку в MaxFlomShop.",

                read:
                    false,

                createdAt:
                    serverTimestamp(),

                fromAdmin:
                    true

            }
        );


        adminNotice(
            "Заказ отмечен как выполненный. Покупатель получил сообщение.",
            "success"
        );


        await loadAdminOrders();


    }catch(error){

        adminNotice(
            "Не удалось выполнить заказ: " +
            firebaseError(error),
            "error"
        );

    }

};


/* =========================================================
   CANCEL ORDER
========================================================= */

window.cancelOrder =
async function(
    orderId,
    userId
){

    if(!checkAdmin())
        return;


    try{

        await updateDoc(
            doc(
                db,
                "orders",
                orderId
            ),
            {

                status:
                    "cancelled",

                cancelledAt:
                    serverTimestamp()

            }
        );


        await addDoc(
            collection(
                db,
                "messages"
            ),
            {

                userId:
                    userId,

                text:
                    "Ваш заказ был отменён администратором.",

                read:
                    false,

                createdAt:
                    serverTimestamp(),

                fromAdmin:
                    true

            }
        );


        await loadAdminOrders();


        adminNotice(
            "Заказ отменён.",
            "success"
        );


    }catch(error){

        adminNotice(
            "Ошибка отмены заказа.",
            "error"
        );

    }

};


/* =========================================================
   ADMIN SUPPORT
========================================================= */

window.loadAdminSupport =
async function(){

    if(!checkAdmin())
        return;


    const box =
        document.getElementById(
            "adminSupport"
        );


    box.innerHTML =
        `

        <div class="loading">

            <div class="spinner"></div>

            Загрузка обращений...

        </div>

        `;


    try{

        const q =
            query(
                collection(
                    db,
                    "supportMessages"
                ),
                limit(200)
            );


        const snap =
            await getDocs(q);


        if(snap.empty){

            box.innerHTML =
                `

                <div class="empty">

                    Обращений пока нет.

                </div>

                `;

            return;

        }


        const allMessages = [];


        snap.forEach(item=>{

            allMessages.push({
                id:item.id,
                ...item.data()
            });

        });


        allMessages.sort(
            (a,b)=>
                getTimestamp(a.createdAt) -
                getTimestamp(b.createdAt)
        );


        const users = {};


        allMessages.forEach(message=>{

            const uid =
                message.userId;


            if(!users[uid]){

                users[uid] = [];

            }


            users[uid].push(
                message
            );

        });


        box.innerHTML = "";


        Object.keys(users).forEach(uid=>{

            const messages =
                users[uid];


            const last =
                messages[
                    messages.length - 1
                ];


            const div =
                document.createElement(
                    "div"
                );


            div.className =
                "support-user";


            let chatHtml = "";


            messages.forEach(message=>{

                chatHtml += `

                    <div
                        class="support-message ${
                            message.fromAdmin
                            ? "admin"
                            : "user"
                        }">

                        <div class="support-label">

                            ${
                                message.fromAdmin
                                ? "👨‍💼 Администратор"
                                : "👤 Покупатель"
                            }

                        </div>

                        ${escapeHtml(
                            message.text || ""
                        )}

                    </div>

                `;

            });


            div.innerHTML = `

                <div
                    class="support-user-head">

                    <div>

                        <b>
                            👤 Покупатель
                        </b>

                        <br>

                        <small>
                            UID:
                            ${escapeHtml(uid)}
                        </small>

                        <br>

                        <small>
                            Email:
                            ${escapeHtml(
                                last.email || ""
                            )}
                        </small>

                    </div>

                </div>


                <div class="support-chat">

                    ${chatHtml}

                </div>


                <textarea
                    id="reply-${uid}"
                    placeholder="Ответить этому покупателю...">
                </textarea>


                <button
                    class="btn purple"
                    onclick="replySupport('${uid}')">

                    📤 Ответить

                </button>

            `;


            box.appendChild(div);

        });


    }catch(error){

        box.innerHTML =
            `

            <div class="notice error">

                Ошибка загрузки поддержки:

                <br><br>

                ${escapeHtml(
                    firebaseError(error)
                )}

            </div>

            `;

    }

};


/* =========================================================
   ADMIN REPLY SUPPORT
========================================================= */

window.replySupport =
async function(userId){

    if(!checkAdmin())
        return;


    const textarea =
        document.getElementById(
            "reply-" + userId
        );


    if(!textarea)
        return;


    const text =
        textarea.value.trim();


    if(!text){

        adminNotice(
            "Введите ответ.",
            "error"
        );

        return;

    }


    try{

        await addDoc(
            collection(
                db,
                "supportMessages"
            ),
            {

                userId:
                    userId,

                text:
                    text,

                fromAdmin:
                    true,

                read:
                    false,

                createdAt:
                    serverTimestamp()

            }
        );


        /*
        Дополнительно создаём
        обычное уведомление.
        Поэтому ответ будет виден
        и в «Поддержке», и в
        «Сообщениях».
        */

        await addDoc(
            collection(
                db,
                "messages"
            ),
            {

                userId:
                    userId,

                text:
                    "💬 Ответ поддержки: " +
                    text,

                read:
                    false,

                fromAdmin:
                    true,

                createdAt:
                    serverTimestamp()

            }
        );


        adminNotice(
            "Ответ отправлен покупателю.",
            "success"
        );


        await loadAdminSupport();


    }catch(error){

        adminNotice(
            "Не удалось отправить ответ: " +
            firebaseError(error),
            "error"
        );

    }

};


/* =========================================================
   ADMIN DEPOSITS
========================================================= */

window.loadDeposits =
async function(){

    if(!checkAdmin())
        return;


    const box =
        document.getElementById(
            "adminDeposits"
        );


    box.innerHTML =
        `

        <div class="loading">

            <div class="spinner"></div>

            Загрузка заявок...

        </div>

        `;


    try{

        const q =
            query(
                collection(
                    db,
                    "depositRequests"
                ),
                limit(100)
            );


        const snap =
            await getDocs(q);


        if(snap.empty){

            box.innerHTML =
                `

                <div class="empty">

                    Заявок нет.

                </div>

                `;

            return;

        }


        const deposits = [];


        snap.forEach(item=>{

            deposits.push({
                id:item.id,
                ...item.data()
            });

        });


        deposits.sort(
            (a,b)=>
                getTimestamp(b.createdAt) -
                getTimestamp(a.createdAt)
        );


        box.innerHTML = "";


        deposits.forEach(data=>{

            const div =
                document.createElement(
                    "div"
                );


            div.className =
                "order";


            const statusClass =
                data.status === "approved"
                ? "done"
                : data.status === "rejected"
                ? "cancelled"
                : "pending";


            const statusText =
                data.status === "approved"
                ? "Подтверждено"
                : data.status === "rejected"
                ? "Отклонено"
                : "Ожидает";


            div.innerHTML = `

                <div class="order-head">

                    <div>

                        <b>
                            ${Number(
                                data.amount || 0
                            )} ₽
                        </b>

                        <br>

                        <small>

                            UID:
                            ${escapeHtml(
                                data.userId || ""
                            )}

                        </small>

                    </div>


                    <span
                        class="status ${statusClass}">

                        ${statusText}

                    </span>

                </div>


                <div class="order-body">

                    Email:

                    ${escapeHtml(
                        data.email || ""
                    )}

                    <br>

                    Комментарий:

                    ${escapeHtml(
                        data.comment || "—"
                    )}

                    <br>

                    Фото:

                    ${
                        data.hasPhoto
                        ? "Есть"
                        : "Не прикреплено"
                    }

                    <br><br>


                    <button
                        class="btn green"
                        onclick="approveDeposit(
                            '${data.id}',
                            '${data.userId}',
                            ${Number(data.amount || 0)}
                        )"
                        ${data.status !== "pending" ? "disabled" : ""}>

                        ✓ Подтвердить

                    </button>


                    <button
                        class="btn red"
                        onclick="rejectDeposit(
                            '${data.id}',
                            '${data.userId}'
                        )"
                        ${data.status !== "pending" ? "disabled" : ""}>

                        ✕ Отклонить

                    </button>

                </div>

            `;


            box.appendChild(div);

        });


    }catch(error){

        box.innerHTML =
            `

            <div class="notice error">

                Ошибка загрузки заявок:

                <br><br>

                ${escapeHtml(
                    firebaseError(error)
                )}

            </div>

            `;

    }

};


/* =========================================================
   APPROVE DEPOSIT
========================================================= */

window.approveDeposit =
async function(
    requestId,
    userId,
    amount
){

    if(!checkAdmin())
        return;


    try{

        const userRef =
            doc(
                db,
                "users",
                userId
            );


        const userSnap =
            await getDoc(
                userRef
            );


        if(!userSnap.exists()){

            adminNotice(
                "Пользователь не найден.",
                "error"
            );

            return;

        }


        const oldBalance =
            Number(
                userSnap.data().balance || 0
            );


        await updateDoc(
            userRef,
            {
                balance:
                    oldBalance +
                    amount
            }
        );


        await updateDoc(
            doc(
                db,
                "depositRequests",
                requestId
            ),
            {

                status:
                    "approved",

                approvedAt:
                    serverTimestamp()

            }
        );


        await addDoc(
            collection(
                db,
                "messages"
            ),
            {

                userId:
                    userId,

                text:
                    `Ваше пополнение на ${amount} ₽ подтверждено. Деньги зачислены на баланс.`,

                read:
                    false,

                createdAt:
                    serverTimestamp(),

                fromAdmin:
                    true

            }
        );


        await loadDeposits();


        adminNotice(
            "Пополнение подтверждено.",
            "success"
        );


    }catch(error){

        adminNotice(
            "Ошибка подтверждения пополнения: " +
            firebaseError(error),
            "error"
        );

    }

};


/* =========================================================
   REJECT DEPOSIT
========================================================= */

window.rejectDeposit =
async function(
    requestId,
    userId
){

    if(!checkAdmin())
        return;


    try{

        await updateDoc(
            doc(
                db,
                "depositRequests",
                requestId
            ),
            {

                status:
                    "rejected",

                rejectedAt:
                    serverTimestamp()

            }
        );


        await addDoc(
            collection(
                db,
                "messages"
            ),
            {

                userId:
                    userId,

                text:
                    "Ваша заявка на пополнение была отклонена администратором.",

                read:
                    false,

                createdAt:
                    serverTimestamp(),

                fromAdmin:
                    true

            }
        );


        await loadDeposits();


        adminNotice(
            "Заявка отклонена.",
            "success"
        );


    }catch(error){

        adminNotice(
            "Ошибка отклонения заявки: " +
            firebaseError(error),
            "error"
        );

    }

};


/* =========================================================
   MODALS
========================================================= */

window.openModal =
function(id){

    const element =
        document.getElementById(id);


    if(element){

        element.classList.remove(
            "hidden"
        );

    }

};


window.closeModal =
function(id){

    const element =
        document.getElementById(id);


    if(element){

        element.classList.add(
            "hidden"
        );

    }

};


/* =========================================================
   AUTH MODAL
========================================================= */

window.openAuth =
function(){

    document
        .getElementById(
            "authEmail"
        )
        .value = "";


    document
        .getElementById(
            "authPassword"
        )
        .value = "";


    document
        .getElementById(
            "authNotice"
        )
        .innerHTML = "";


    openModal(
        "authModal"
    );

};


/* =========================================================
   NOTICES
========================================================= */

function notice(
    text,
    type=""
){

    const box =
        document.getElementById(
            "globalNotice"
        );


    box.innerHTML =
        `

        <div class="notice ${type}">

            ${escapeHtml(text)}

        </div>

        `;


    setTimeout(
        ()=>{

            box.innerHTML = "";

        },
        5000
    );

}


function authMessage(
    text
){

    document
        .getElementById(
            "authNotice"
        )
        .innerHTML =

        `

        <div class="notice error">

            ${escapeHtml(text)}

        </div>

        `;

}


function adminNotice(
    text,
    type=""
){

    document
        .getElementById(
            "adminNotice"
        )
        .innerHTML =

        `

        <div class="notice ${type}">

            ${escapeHtml(text)}

        </div>

        `;

}


/* =========================================================
   TIMESTAMP HELPER
========================================================= */

function getTimestamp(
    timestamp
){

    if(!timestamp)
        return 0;


    if(
        typeof timestamp.toMillis ===
        "function"
    ){

        return timestamp.toMillis();

    }


    if(
        timestamp.seconds
    ){

        return timestamp.seconds * 1000;

    }


    return 0;

}


/* =========================================================
   FIREBASE ERRORS
========================================================= */

function firebaseError(
    error
){

    const code =
        error?.code || "";


    const errors = {

        "auth/email-already-in-use":
            "Этот email уже используется.",

        "auth/invalid-email":
            "Некорректный email.",

        "auth/weak-password":
            "Слишком слабый пароль.",

        "auth/invalid-credential":
            "Неверный email или пароль.",

        "auth/user-not-found":
            "Пользователь не найден.",

        "auth/wrong-password":
            "Неверный пароль.",

        "permission-denied":
            "Нет разрешения Firestore.",

        "failed-precondition":
            "Firebase требует дополнительную настройку."

    };


    return (
        errors[code] ||
        error?.message ||
        "Произошла ошибка."
    );

}


/* =========================================================
   ESCAPE HTML
========================================================= */

function escapeHtml(
    value
){

    return String(
        value ?? ""
    )

        .replaceAll(
            "&",
            "&amp;"
        )

        .replaceAll(
            "<",
            "&lt;"
        )

        .replaceAll(
            ">",
            "&gt;"
        )

        .replaceAll(
            '"',
            "&quot;"
        )

        .replaceAll(
            "'",
            "&#039;"
        );

}

</script>

</body>
</html>

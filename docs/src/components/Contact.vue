<style lang="less">

@import "../assets/variables.less";
[id]#contact {
    border-left-color: @lila;
    height: auto;
    min-height: 0;
    padding: 0;
    .imprint {
        background: @lila;
        padding: 20px 20px 50px;
        color: @lightgray;
        font-size: 14px;
        .claim {
            color: @orange;
            padding-top: 30px;
        }
        a {
            color: @white;
        }
        p {
          margin-bottom: 15px;
        }
        b {
            font-weight: normal;
            text-transform: uppercase;
            color: @orange;
        }
        ul {
            list-style: none;
            padding: 0;
            margin: 0;
            li {
                margin: 0;
                padding: 10px 0 0;
            }
        }
        >p>img {
            max-width: 90%;
        }
    }
}

@media (min-width: 768px) {
    [id]#contact {
        .imprint {
            padding: 40px 40px 60px;
            .logo {
                float: right;
            }
        }
    }
}

@media (min-width: 1200px) {
    [id]#contact {
        .imprint {
            position: relative;
            height: 200px;
            .logo {
                position: absolute;
                left: 60px;
                top: 60px;
            }
            .links {
                position: absolute;
                left: 30%;
                top: 60px;
            }
            .claim {
                position: absolute;
                left: 60%;
                bottom: 100px;
            }
        }
    }
}

</style>

<template>

<section id="contact">
    <div class="imprint">
        <p class="logo"><img src="../assets/logo_300.png" alt="Logo Piratenpartei Bayern"></p>
        <p class="links"><b>Piratenpartei Bayern</b>
            <nav>
                <ul>
                    <li><a href="https://www.piratenpartei.de/">www.piratenpartei.de</a></li>
                    <li><a href="https://www.piratenpartei.de/kontakt/">Kontakt</a></li>
                    <li><a href="https://www.piratenpartei.de/kontakt/impressum/">Impressum</a></li>
                </ul>
            </nav>
        </p>
        <p class="claim">Piraten. Freu dich aufs Neuland.</p>
    </div>
</section>

</template>

<script>

export default {
    name: 'Contact'
};

</script>

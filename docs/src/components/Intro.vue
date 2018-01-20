<style lang="less">
@import "../assets/variables.less";
[id]#intro {
    border-left-color: @orange;
    background-color: fade(@lightgray, 70%);
    overflow: hidden;

    p {
        margin: 0 0 10px;
    }

    img.avatar {
        margin: 10px 20px 20px 10px;
        float: left;
        width: 100px;
        height: 100px;
        border-radius: 100px;
        border: 3px solid @white;
        box-shadow: 0 0 0 5px @black;
    }

    .no-col-break {
        -webkit-column-break-inside: avoid;
        page-break-inside: avoid;
        break-inside: avoid;
    }

    .orderlink {
      text-align: center;
      padding: 10px 0;
      a {
        color: @lila;
        font-weight: bold;
      }
    }
}

@media (min-width: 768px) {
    [id]#intro {
        column-count: 2;
        column-gap: 20px;
    }
}

@media (min-width: 1200px) {
    [id]#intro {
        column-count: 3;
    }
}
</style>

<template>
<section id="intro">
    <p :style="textStyle">
        Kaum ist das Jahr 2017 rum geht es auch schon auf die nächsten Feiertage zu. Am 14. Februar 2018 erwarten uns gleich zwei besondere Tage: Neben dem Valentinstag ist zugleich auch Aschermittwoch.
        <br>An zweiterem liefern sich tradionell seit vielen Jahren vor allem in Bayern verschiedene politische Parteien einen rhetorischen Schlagabtausch.
    </p>
    <p :style="textStyle">
        Auch in diesem Jahr lädt der <a href="https://piratenpartei-bayern.de">Landesverband Bayern der Piratenpartei Deutschland</a> wieder zum <b>piratigen Aschermittwoch</b> in <b>Straubing</b> ein.
        <br>Willkommen sind alle Interessierten, Sympathisanten, Freunde und natürlich auch Mitglieder der Piratenpartei.
    </p>
    <p :style="textStyle" class="no-col-break">
        <img src="../assets/speaker/Martina_Wenta_Icon.jpg" alt="Astrid Semm" class="avatar" />
        <b>Martina Wenta</b>
        <icon-link icon="twitter" href="https://twitter.com/mertl0rn" title="@mertl0rn" />
        <icon-link icon="facebook" href="https://www.facebook.com/Mertl0r" title="Martina Michaela Wenta" />, Bezirksrätin der Piratenpartei in Oberbayern, wird den Nachmittag im <b>Magnobonus-Markmiller-Saal</b> moderieren.
    </p>
    <p :style="textStyle">
        Als Redner dürfen wir uns auf verschiedene aktuelle und ehemalige politische Geschäftsführer*innen verschiedener Gliederungen der Piratenpartei freuen.
    </p>
    <p :style="textStyle">
        Der Eintritt ist selbstverständlich Kostenlos. Der Verzehr von selbst mitgebrachten Speisen und Getränken ist leider nicht gestattet.
    </p>
    <p :style="textStyle">
        Es wird ebenfalls wieder ein Fischgericht geben.
    </p>
    <p :style="textStyle" align="center">
        &nbsp;<br><b>Bio-Lachssteak</b><br>wahlweise mit<br>Rosmarin- oder Petersilien-Kartoffeln,<br>Zitronen-Dill-Soße und Gemüse<br><br>für <b>10,80 €</b> <small>inkl. MwSt</small><br>&nbsp;
    </p>
    <p :style="textStyle">
        Zur besseren Planung ist hierfür eine verbindliche <b>Anmeldung</b> bis spätestens 7. Februar 2018 erforderlich.
    </p>
    <div :style="orderLinkStyle" class="orderlink">
      &raquo;
      <a href="https://form.jotformeu.com/80011658583355">Zum Anmeldeformular</a>
      &laquo;
    </div>
    <p :style="textStyle">
        Alternativ gibt es ohne Vorbestellung vor Ort auch Schnitzel.
    </p>
</section>
</template>

<script>
import IconLink from '@/components/IconLink';

export default {
    name: 'Intro',
    components: {
        IconLink
    },
    data() {
        return {
            textStyle: {
                opacity: 1
            },
            orderLinkStyle: {
              opacity: 1,
              textIndent: 0
            },
            bounced: false
        }
    },
    methods: {
        handleScroll() {
            const offset = document.getElementById('wallpaper').clientHeight +
                (window.innerHeight * 0.6);
            const scrollBottom = window.scrollY + window.innerHeight;
            this.textStyle.opacity = 1 - Math.min(1, Math.max(0, (offset - scrollBottom) / window.innerHeight * 5));
            this.orderLinkStyle.opacity = this.textStyle.opacity;

            if(this.textStyle.opacity >= 1 && !this.bounced) {
              this.bounced = true;

console.log('bounce');
              this.orderLinkStyle.textIndent = '-5px';
              window.setTimeout(() => this.orderLinkStyle.textIndent = '-2px', 50);
              window.setTimeout(() => this.orderLinkStyle.textIndent = '0px', 100);
              window.setTimeout(() => this.orderLinkStyle.textIndent = '1px', 150);
              window.setTimeout(() => this.orderLinkStyle.textIndent = '3px', 200);
              window.setTimeout(() => this.orderLinkStyle.textIndent = '0px', 250);
              window.setTimeout(() => this.orderLinkStyle.textIndent = '-2px', 300);
              window.setTimeout(() => this.orderLinkStyle.textIndent = '1px', 350);
              window.setTimeout(() => this.orderLinkStyle.textIndent = '5px', 400);
              window.setTimeout(() => this.orderLinkStyle.textIndent = '1px', 450);
              window.setTimeout(() => this.orderLinkStyle.textIndent = '-3px', 500);
              window.setTimeout(() => this.orderLinkStyle.textIndent = '0px', 550);
              window.setTimeout(() => this.orderLinkStyle.textIndent = '4px', 600);
            } else if(this.textStyle.opacity < 1 && this.bounced) {
              this.bounced = false;
            }
        }
    },
    created() {
        window.addEventListener('scroll', this.handleScroll);
    },
    destroyed() {
        window.removeEventListener('scroll', this.handleScroll);
    }
};
</script>

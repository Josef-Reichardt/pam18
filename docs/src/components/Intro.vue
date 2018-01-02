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
        <icon-link icon="facebook" href="https://www.facebook.com/Mertl0r" title="Martina Michaela Wenta" />, Justizwachtmeisterin am Landgericht Traunstein und seit 2013 für die PIRATEN im Bezirkstag Oberbayern, wird den Nachmittag im <b>Magnobonus-Markmiller-Saal</b> moderieren.
    </p>
    <p :style="textStyle">
        Als Redner dürfen wir uns auf verschiedene aktuelle und ehemalige politische Geschäftsführer*innen verschiedener Gliederungen der Piratenpartei freuen.
    </p>
    <p :style="textStyle">
        Der Eintritt ist selbstverständlich Kostenlos. Der Verzehr von selbst mitgebrachten Speißen und Getränken ist leider nicht gestattet.
    </p>
    <p :style="textStyle">
        Es wird ebenfalls wieder ein Fischgericht geben. Leider stehen zum aktuellen Zeitpunkt noch nicht alle Details zur Art und zum Umfang des Gerichtes fest. Bis auf weiteres handelt es sich also um:
    </p>
    <p :style="textStyle" align="center">
        <b>Überraschungs-Fisch-Gericht</b><br> mit Überraschungs-Beilage<br> für <b>??,?? €</b> <small>inkl. MwSt</small>
    </p>
    <p :style="textStyle">
        Zur besseren Planung ist hierfür eine verbindliche Anmeldung erforderlich. &raquo; <a href="https://form.jotformeu.com/80011658583355">Zum Anmeldeformular</a>
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
            }
        }
    },
    methods: {
        handleScroll() {
            const offset = document.getElementById('wallpaper').clientHeight +
                (document.getElementById('intro').clientHeight * 0.5);
            const scrollBottom = window.scrollY + window.innerHeight;
            this.textStyle.opacity = 1 - Math.min(1, Math.max(0, (offset - scrollBottom) / window.innerHeight * 5));
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

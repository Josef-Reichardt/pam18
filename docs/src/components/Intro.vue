<style lang="less">
@import "../assets/variables.less";
[id]#intro {
    border-left-color: @orange;
    background-color: fade(@lightgray, 70%);

    p {
      margin: 0 0 10px 0;
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
  <p>
    Kaum ist das Jahr 2017 rum geht es auch schon auf die nächsten Feiertage zu. Am 14. Februar 2018 erwarten uns gleich zwei besondere Tage: Neben dem Valentinstag ist zugleich auch Aschermittwoch.
    <br>An zweiterem liefern sich tradionell seit vielen Jahren vor allem in Bayern verschiedene politische Parteien einen rhetorischen Schlagabtausch.
  </p>
  <p>
    Auch in diesem Jahr lädt der <a href="https://piratenpartei-bayern.de">Landesverband Bayern der Piratenpartei Deutschland</a> wieder zum <b>piratigen Aschermittwoch</b> in <b>Straubing</b> ein.
    <br>Willkommen sind alle Interessierten, Sympathisanten, Freunde und natürlich auch Mitglieder der Piratenpartei.
  </p>
  <p class="no-col-break">
    <img src="../assets/speaker/Martina_Wenta_Icon.jpg" alt="Astrid Semm" class="avatar" />
    <b>Martina Wenta</b>
    <a href="https://twitter.com/mertl0rn" class="twitter"><span>@mertl0rn</span></a>
    <a href="https://www.facebook.com/Mertl0r" class="facebook"><span>Martina Michaela Wenta</span></a>, Justizwachtmeisterin am Landgericht Traunstein und seit 2013 für die PIRATEN im Bezirkstag Oberbayern, wird den Nachmittag im <b>Magnobonus-Markmiller-Saal</b>    moderieren.
  </p>
  <p>
    Als Redner dürfen wir uns auf verschiedene aktuelle und ehemalige politische Geschäftsführer*innen verschiedener Gliederungen der Piratenpartei freuen.
  </p>
</section>
</template>

<script>
export default {
  name: 'Intro'
};
</script>

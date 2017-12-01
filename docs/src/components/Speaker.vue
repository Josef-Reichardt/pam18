<style scoped lang="less">
@import "../assets/variables.less";
[id]#speaker {
    border-left-color: @lightgray;

    ul {
      list-style: none;
      padding: 0;
      margin: 20px 0 0;

      li {
        padding: 30px 20px 0 160px;
        margin: 0 0 20px;
        position: relative;
        min-height: 100px;

        img {
          position: absolute;
          top: 0;
          left: 20px;
          width: 100px;
          height: 100px;
          border-radius: 100px;
          border: 3px solid @white;
          box-shadow: 0 0 0 5px @black;
        }
      }
    }
}
</style>

<template>
<section id="speaker">
  <h3>Redner?</h3>

  <ul>
    <li>
      <img src="../assets/speaker/Astrid_Semm_Icon.jpg" alt="Astrid Semm" />
      <strong>Astrid Semm</strong><br>
      Stellvertretende Politische Geschäftsführerin, Piratenpartei Deutschland
    </li>
      <li>
        <img src="../assets/speaker/Piratenlily_Icon.jpg" alt="Astrid Semm" />
        <strong>Piratenlily</strong><br>
        Ehemalige Politische Geschäftsführerin, Piratenpartei Deutschland
      </li>
        <li>
          <img src="../assets/speaker/Benjamin_Wildenauer_Icon.jpg" alt="Astrid Semm" />
          <strong>Benjamin Wildenauer</strong><br>
          Stellvertretender Politischer Geschäftsführer, Piratenpartei Bayern
        </li>
  </ul>
</section>
</template>

<script>
export default {
  name: 'Speaker'
};
</script>

<template>
  <div class="content">
    <ul>
      <li v-for="subject in subjects">
        {{subject.name}}: 
      <li class="grades" v-for="grade in subject.grades">
        {{grade}}, 
      </li>
      Ø {{subjectAverage(subject.grades)}}
      </li>
    </ul>
    <h4>Gesammtdurchschnitt: {{overallAverage}}</h4>
    <h4> Mangelpunkte: {{flaws}}</h4>
  </div>
</template>

<script>

export default {
  name: 'App',
  data: function(){
    return{
      subjects: [
    {
        name: "Mathematik",
        grades: [5,4.7,3.5,4.1] 
    },
    {
        name: "Geschichte",
        grades: [5.5,4.9,5.75] 
    },
    {
        name: "Physik",
        grades: [2,2.7,4.3] 
    },
    {
        name: "Deutsch",
        grades: [4.25,4.1,3.5] 
    },
]

    }
  },
  methods: {
    subjectAverage: function(grades){
      var total = 0;

      grades.forEach(grade => {
        total += grade;
      });

      return Math.round(total / grades.length *2)/2;
    }
  },
  computed: {
    overallAverage: function(){
      var total = 0;

      this.subjects.forEach(subject =>{
        total += parseFloat(this.subjectAverage(subject.grades));
      });

      return total / this.subjects.length;
    },
    flaws: function(){
      var count = 0;

      this.subjects.forEach(subject =>{
        var grade = parseFloat(this.subjectAverage(subject.grades));

        if( grade < 4){
          count ++;
        }
      });

      return count;
    }
  }
}
</script>


<style lang="scss">

.content{
  width: 800px;
  margin: 0 auto;
}

.grades{
  display: inline;
}
</style>
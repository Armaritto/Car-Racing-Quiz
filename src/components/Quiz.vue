<template>
  <div class="main-class">
    <div class="question-partition">
      qi
    </div>
    <div class="scores-partition">
      <div></div>
      <div>
        <div @click="open1b" class="jumping-object1b" :style="{ width: objectWidth + 'px', height: objectWidth + 'px', bottom: correctAnswers1b === totalQuestions ? maxHeight + 'px' : step * correctAnswers1b + 'px' }"></div>
      </div>
      <div>
        <div @click="open1g" class="jumping-object1g" :style="{ width: objectWidth + 'px', height: objectWidth + 'px', bottom: correctAnswers1g === totalQuestions ? maxHeight + 'px' : step * correctAnswers1g + 'px' }"></div>
      </div>
      <div>
        <div @click="open2b" class="jumping-object2b" :style="{ width: objectWidth + 'px', height: objectWidth + 'px', bottom: correctAnswers2b === totalQuestions ? maxHeight + 'px' : step * correctAnswers2b + 'px' }"></div>
      </div>
      <div>
        <div @click="open2g" class="jumping-object2g" :style="{ width: objectWidth + 'px', height: objectWidth + 'px', bottom: correctAnswers2g === totalQuestions ? maxHeight + 'px' : step * correctAnswers2g + 'px' }"></div>
      </div>
      <div>
        <div @click="open3b" class="jumping-object3b" :style="{ width: objectWidth + 'px', height: objectWidth + 'px', bottom: correctAnswers3b === totalQuestions ? maxHeight + 'px' : step * correctAnswers3b + 'px' }"></div>
      </div>
      <div>
        <div @click="open3g" class="jumping-object3g" :style="{ width: objectWidth + 'px', height: objectWidth + 'px', bottom: correctAnswers3g === totalQuestions ? maxHeight + 'px' : step * correctAnswers3g + 'px' }"></div>
      </div>
      <div></div>
    </div>
  </div>
</template>

<script>
import swal from 'sweetalert2';
export default {
  name: 'Quiz',
  props: {
    msg: String
  },
  data() {
    return {
      correctAnswers1b: 0,
      correctAnswers2b: 0,
      correctAnswers3b: 0,
      correctAnswers1g: 0,
      correctAnswers2g: 0,
      correctAnswers3g: 0,
      totalQuestions: 11, // number of questions + 1
      maxHeight: 0
    }
  },
  created() {
    this.maxHeight = window.innerHeight - 5;
  },
  computed: {
    step() {
      return this.maxHeight / this.totalQuestions;
    },
    objectWidth() {
      return 0.0351493848857645 * window.innerWidth;
    },
  },
  methods: {
    open1b(){
      swal.fire({
        title: "أولى ولاد",
        showDenyButton: true,
        showCancelButton: false,
        confirmButtonText: "+",
        denyButtonText: `-`
      }).then((result) => {
        if (result.isConfirmed) {
          this.answerQuestion1b(true);
        } else if (result.isDenied) {
          this.decreaseAnswer1b();
        }
      });
    },
    open2b(){
      swal.fire({
        title: "تانية ولاد",
        showDenyButton: true,
        showCancelButton: false,
        confirmButtonText: "+",
        denyButtonText: `-`
      }).then((result) => {
        if (result.isConfirmed) {
          this.answerQuestion2b(true);
        } else if (result.isDenied) {
          this.decreaseAnswer2b();
        }
      });
    },
    open3b(){
      swal.fire({
        title: "تالتة ولاد",
        showDenyButton: true,
        showCancelButton: false,
        confirmButtonText: "+",
        denyButtonText: `-`
      }).then((result) => {
        if (result.isConfirmed) {
          this.answerQuestion3b(true);
        } else if (result.isDenied) {
          this.decreaseAnswer3b();
        }
      });
    },
    open1g(){
      swal.fire({
        title: "أولى بنات",
        showDenyButton: true,
        showCancelButton: false,
        confirmButtonText: "+",
        denyButtonText: `-`
      }).then((result) => {
        if (result.isConfirmed) {
          this.answerQuestion1g(true);
        } else if (result.isDenied) {
          this.decreaseAnswer1g();
        }
      });
    },
    open2g(){
      console.log(60/window.innerWidth);
      swal.fire({
        title: "تانية بنات",
        showDenyButton: true,
        showCancelButton: false,
        confirmButtonText: "+",
        denyButtonText: `-`
      }).then((result) => {
        if (result.isConfirmed) {
          this.answerQuestion2g(true);
        } else if (result.isDenied) {
          this.decreaseAnswer2g();
        }
      });
    },
    open3g(){
      swal.fire({
        title: "تالتة بنات",
        showDenyButton: true,
        showCancelButton: false,
        confirmButtonText: "+",
        denyButtonText: `-`
      }).then((result) => {
        if (result.isConfirmed) {
          this.answerQuestion3g(true);
        } else if (result.isDenied) {
          this.decreaseAnswer3g();
        }
      });
    },
    answerQuestion1b(isCorrect) {
      if (isCorrect) {
        if (this.correctAnswers1b === this.totalQuestions - 1) {
          return;
        }
        this.correctAnswers1b++;
        const jumpingObject = document.querySelector('.jumping-object1b');
        jumpingObject.classList.remove('jump');
        void jumpingObject.offsetWidth;
        jumpingObject.classList.add('jump');
      }
    },
    decreaseAnswer1b() {
      if (this.correctAnswers1b > 0) {
        this.correctAnswers1b--;
        const jumpingObject = document.querySelector('.jumping-object1b');
        jumpingObject.classList.remove('jump');
        void jumpingObject.offsetWidth;
        jumpingObject.classList.add('jump');
      }
    },
    answerQuestion2b(isCorrect) {
      if (isCorrect) {
        if (this.correctAnswers2b === this.totalQuestions - 1) {
          return;
        }
        this.correctAnswers2b++;
        const jumpingObject = document.querySelector('.jumping-object2b');
        jumpingObject.classList.remove('jump');
        void jumpingObject.offsetWidth;
        jumpingObject.classList.add('jump');
      }
    },
    decreaseAnswer2b() {
      if (this.correctAnswers2b > 0) {
        this.correctAnswers2b--;
        const jumpingObject = document.querySelector('.jumping-object2b');
        jumpingObject.classList.remove('jump');
        void jumpingObject.offsetWidth;
        jumpingObject.classList.add('jump');
      }
    },
    answerQuestion3b(isCorrect) {
      if (isCorrect) {
        if (this.correctAnswers3b === this.totalQuestions - 1) {
          return;
        }
        this.correctAnswers3b++;
        const jumpingObject = document.querySelector('.jumping-object3b');
        jumpingObject.classList.remove('jump');
        void jumpingObject.offsetWidth;
        jumpingObject.classList.add('jump');
      }
    },
    decreaseAnswer3b() {
      if (this.correctAnswers3b > 0) {
        this.correctAnswers3b--;
        const jumpingObject = document.querySelector('.jumping-object3b');
        jumpingObject.classList.remove('jump');
        void jumpingObject.offsetWidth;
        jumpingObject.classList.add('jump');
      }
    },
    answerQuestion1g(isCorrect) {
      if (isCorrect) {
        if (this.correctAnswers1g === this.totalQuestions - 1) {
          return;
        }
        this.correctAnswers1g++;
        const jumpingObject = document.querySelector('.jumping-object1g');
        jumpingObject.classList.remove('jump');
        void jumpingObject.offsetWidth;
        jumpingObject.classList.add('jump');
      }
    },
    decreaseAnswer1g() {
      if (this.correctAnswers1g > 0) {
        this.correctAnswers1g--;
        const jumpingObject = document.querySelector('.jumping-object1g');
        jumpingObject.classList.remove('jump');
        void jumpingObject.offsetWidth;
        jumpingObject.classList.add('jump');
      }
    },
    answerQuestion2g(isCorrect) {
      if (isCorrect) {
        if (this.correctAnswers2g === this.totalQuestions - 1) {
          return;
        }
        this.correctAnswers2g++;
        const jumpingObject = document.querySelector('.jumping-object2g');
        jumpingObject.classList.remove('jump');
        void jumpingObject.offsetWidth;
        jumpingObject.classList.add('jump');
      }
    },
    decreaseAnswer2g() {
      if (this.correctAnswers2g > 0) {
        this.correctAnswers2g--;
        const jumpingObject = document.querySelector('.jumping-object2g');
        jumpingObject.classList.remove('jump');
        void jumpingObject.offsetWidth;
        jumpingObject.classList.add('jump');
      }
    },
    answerQuestion3g(isCorrect) {
      if (isCorrect) {
        if (this.correctAnswers3g === this.totalQuestions - 1) {
          return;
        }
        this.correctAnswers3g++;
        const jumpingObject = document.querySelector('.jumping-object3g');
        jumpingObject.classList.remove('jump');
        void jumpingObject.offsetWidth;
        jumpingObject.classList.add('jump');
      }
    },
    decreaseAnswer3g() {
      if (this.correctAnswers3g > 0) {
        this.correctAnswers3g--;
        const jumpingObject = document.querySelector('.jumping-object3g');
        jumpingObject.classList.remove('jump');
        void jumpingObject.offsetWidth;
        jumpingObject.classList.add('jump');
      }
    },
  }
}
</script>

<style scoped>
.main-class {
  display: flex;
  justify-content: space-around;
  width: 99%;
}

.question-partition {
  flex: 0 0 63%;
}

.scores-partition {
  flex: 0 0 37%;
  display: flex;
  justify-content: space-evenly;
  align-items: flex-end;
  height: 98vh;
  background: #292525;
  background: url(road.png) repeat;
  background-size: calc(100% / 7);
}

.jumping-object1b{
  position: relative;
  margin-bottom: 5px;
  background: url(car3.png);
  transition: bottom 1s ease-in-out;
  background-size:100%;
}
.jumping-object2b{
  position: relative;
  margin-bottom: 5px;
  background: url(car2.png);
  transition: bottom 1s ease-in-out;
  background-size:100%;
}
.jumping-object3b{
  position: relative;
  margin-bottom: 5px;
  background: url(car1.png);
  transition: bottom 1s ease-in-out;
  background-size:100%;
}
.jumping-object1g{
  position: relative;
  margin-bottom: 5px;
  background: url(car4.png);
  transition: bottom 1s ease-in-out;
  background-size:100%;
}
.jumping-object2g{
  position: relative;
  margin-bottom: 5px;
  background: url(car5.png);
  transition: bottom 1s ease-in-out;
  background-size:100%;
}
.jumping-object3g{
  position: relative;
  margin-bottom: 5px;
  background: url(car6.png);
  transition: bottom 1s ease-in-out;
  background-size:100%;
}

</style>

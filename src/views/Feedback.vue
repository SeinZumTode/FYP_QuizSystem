<template>
  <div class='chat'>
    <el-page-header class="chat__header" @back="goBack">
      <template #content>
        <span class="text-large font-600 mr-3"> Student Feedback </span>
      </template>
      <template #extra>
        <div class="flex items-center">
          <span class="text-large font-600 mr-3"> Welcome, <i>{{ username }} </i></span>

        </div>
      </template>
    </el-page-header>
    <el-container>
      <el-aside width="15%" style="background-color: rgb(238, 241, 246)">
        <el-scrollbar>
          <el-menu :default-openeds="['1', '2']" default-active="2-1">
            <el-menu-item v-for="(item, index) in questions" :key="index" :index="'2-' + (index + 1)"
              @click="openQuestion(index, item)">
              <el-icon>
                <ChatLineSquare />
              </el-icon>Question {{ index + 1 }}
            </el-menu-item>
          </el-menu>
        </el-scrollbar>
      </el-aside>
      <el-main>

        <p class="text-3xl" style="margin-top: 1%">Question {{ ID }}</p>
        <p v-text="questionSelected.body" class="text-xl text-gray-500" style="margin-top: 5%"> </p>
        <el-row>
          <el-col :span="14" class="my-12">
            <el-card shadow="always" class="card">
              <el-breadcrumb separator="|">
                <el-breadcrumb-item class="item">
                  <p class="text-4xl text-blue-500 text-center item"> 70% </p>
                  <p class="text-xl text-gray-600 text-center item">Accuracy</p>
                </el-breadcrumb-item>
                <el-breadcrumb-item class="item">
                  <p class="text-4xl text-green-500 text-center item"> {{ questionSelected.correctAnswer }} </p>
                  <p class="text-xl text-gray-600 text-center item">Correct answer</p>
                </el-breadcrumb-item>
                <el-breadcrumb-item class="item">
                  <p class="text-4xl text-red-500 text-center item" width="50%"> D </p>
                  <p class="text-xl text-gray-600 text-center item" width="50%">Most chosed</p>
                </el-breadcrumb-item>
              </el-breadcrumb>
            </el-card>
          </el-col>
        </el-row>
        <el-col :span="18">
          <el-row style="flex-wrap: nowrap; margin: 5% 0">
            <el-button style="flex-wrap: nowrap; margin-right: 5%;" :disabled="true" color="green">Option A:
            </el-button>
            <el-text class="mt-1" maxlength="30" size="large" v-text="questionSelected.option[0]"></el-text>
          </el-row>

          <el-row style="flex-wrap: nowrap; margin: 5% 0">
            <el-button style="margin-right: 5%;">Option B: </el-button>
            <el-text class="mt-1" maxlength="30" size="large" v-text="questionSelected.option[1]"></el-text>
          </el-row>

          <el-row style="flex-wrap: nowrap; margin: 5% 0">
            <el-button style="margin-right: 5%;">Option C: </el-button>
            <el-text class="mt-1" maxlength="30" size="large" v-text="questionSelected.option[2]"></el-text>
          </el-row>

          <el-row style="flex-wrap: nowrap; margin: 5% 0">
            <el-button style="margin-right: 5%;">Option D: </el-button>
            <el-text class="mt-1" maxlength="30" size="large" v-text="questionSelected.option[3]"></el-text>
          </el-row>
        </el-col>



      </el-main>

    </el-container>
  </div>
</template>


<script>
import { read } from '@popperjs/core';
import Question from '../static/question.json';

export default {
  created() {
    this.questionSelected = this.questions[0];
  },
  components: {

  },
  data() {
    return {
      questions: [
        {
          body: "The programming language 'Swift' was created to replace what other programming language?",
          answer: 2,
          correctAnswer: "B",
          isMultiple: false,
          option: ["Ruby", "Objective-C", "C++", "C#"]
        },
        {
          body: "In computing terms, typically what does CLI stand for?",
          answer: 3,
          correctAnswer: "C",
          isMultiple: false,
          option: ["Common Language Input", "Control Line Interface", "Command Line Interface", "Common Language Interface"]
        },
        {
          body: "What does the computer software acronym JVM stand for?",
          answer: 1,
          correctAnswer: "A",
          isMultiple: false,
          option: ["Java Virtual Machine", "Java Vendor Machine", "Java Visual Machine", "Just Virtual Machine"]
        },
        {
          body: "What does the computer software acronym JVM stand for?",
          answer: 1,
          correctAnswer: "A",
          isMultiple: false,
          option: ["Java Virtual Machine", "Java Vendor Machine", "Java Visual Machine", "Just Virtual Machine"]
        },
      ],
      questionSelected: null,
      ID: 1,
      muted: false,
      username: sessionStorage.getItem('uname')
    }
  },
  methods: {
    goBack() {
      this.$router.push("/");
      
    },
    openQuestion(index, item) {
      this.questionSelected = item;
      this.ID = index + 1;
    },
  }
}


</script>

<style scoped>
.chat {
  display: flex;
  position: relative;
  flex-direction: column;
  justify-content: space-between;
  height: 80%;
  min-height: 800px;
  width: 80%;
  max-width: 1200px;
  background-color: #ffffff;
  margin: 5% auto 0rem;
  border-radius: 1.5rem;
  box-shadow: 0px 1px 20px #9c9cc855;
}

.chat__header {
  background: #ffffff;
  box-shadow: 0px 3px 10px rgba(0, 0, 0, 0.05);
  border-radius: 24px 24px 0px 0px;
  padding: 1.8rem;
  font-size: 20px;
  font-weight: 700;
}


.card {
  display: flex;
  justify-content: center;
  flex-direction: row;
}

.item {
  flex: 1;
  text-align: center;
  margin: 0 10px;
}

.option {
  font-family: Helvetica;
  font-size: 18px;
  line-height: 1.7;
  letter-spacing: tracking-wider;
  flex: 1;
  text-align: center;
}

.option1 {
  font-family: Helvetica;
  font-size: 18px;
  line-height: 1.7;
  letter-spacing: tracking-wider;
  flex: 1;
  text-align: center;

}
</style>
<!-- eslint-disable -->
<template>
<div class="hello">
    <vue-speech @onTranscriptionEnd="onEnd" id="vue-spech" />
    <div class="container">
        <h2 class="jumbo"> Question Answering</h2>
        <p class="desc">
            This is a small cortana. You can ask questions about Economic inequality.
            Karen has a base knowledge about economic inequality.
        </p>
    </div>
    <div class="box flex">
        <div class="container left color">
            <h2 class="contextParaf"> Context Paragraph </h2>
            <div class="paragraph">
                <p class="white paraf"> {{abstract}}</p>
            </div>
        </div>
        <div class="container right">
            <h2 class="contextParaf"> What can I help you with?</h2>
            <div class="form">
                <input v-model="msg" class="input" placeholder="Ask or Tyope a question about Economic Inequality">
                <button v-on:click="getMessage(msg);" class="btn"> Ask question</button>
            </div>
            <h1 v-if="answer" class="contextParaf"> Answer </h1>
            <div class="paragraph">
                <p v-if="answer" class="center paraf">
                    {{answer}}
                </p>
            </div>
        </div>
    </div>

</div>
</template>

<script>
/* eslint-disable */
import axios from 'axios';

const path = 'http://b4b8cf7e0cdd.ngrok.io/api/question';
const path_abs = 'http://b4b8cf7e0cdd.ngrok.io/api/abstract';

export default {
    name: 'Karen',
    data() {
        return {
            msg: '',
            test_question: 'What philosophy of thought addresses wealth inequality?',
            answer: '',
            abstract: '',
            questionAnswered: true,
            MAX_COMPARAPRE: 50, //check how simillar ans and abstract is 
            error: "Sir I Can't find answer to this question. Try economic inequality questions",
            error_manu: 'Ni mod no hay respuesta'
        };
    },
    methods: {
        getMessage(msg) {
            console.log(msg)
            axios.post(path, {
                    question: msg
                })
                .then((res) => {
                    let answer = res.data.answer;
                    let abstract = res.data.abstract;
                    //This means there is no answer to question, therefore ans = abs
                    let ans_len = answer.length
                    let abs_len = abstract.length
                    //console.log(res.data)
                    if ((abs_len - ans_len) <= this.MAX_COMPARAPRE || this.msg == answer ||
                        answer.includes("CLS") || this.answer.includes("SEP") ||
                        this.answer.includes("[SEP]") || this.answer.includes("[CLS]")) // really similar
                    {
                        this.answer = '';
                        this.sayit(this.error_manu)
                    } else {
                        this.answer = answer
                        this.abstract = abstract
                        this.sayit(this.answer)
                    }
                })
                .catch((error) => {
                    console.error(error);
                });
        },

        getAbstract() {
            axios.get(path_abs, {})
                .then((res) => {
                    this.$data.abstract = res.data
                }).catch((error) => {
                    console.error(error);
                });
        },
        //TTS, return speach
        sayit(text) {
            let utterance = new SpeechSynthesisUtterance(text);
            utterance.rate = .9 //speed
            utterance.lang = 'en-US';
            speechSynthesis.speak(utterance);
        },
        onEnd({
            lastSentence,
            transcription
        }) {
            // `lastSentence` is the last sentence before the pause
            // `transcription` is the full array of sentences
            //console.log(transcription);
            this.msg = lastSentence
            this.getMessage(this.msg)

        }
    },
    created() {
        console.log("created");
        if (!'speechSynthesis' in window) {
            alert("TTS not suported")
        }
    },
    mounted() {
        this.getAbstract()
    }
};
</script>
<!-- Add "scoped" attribute to limit CSS to this component only -->

<style scoped>
.paragraph {
    width: 100%;
    padding: 10px;
}

.center {
    text-align: center !important;
}

.btn {
    background-color: #16a085;
    border: none;
    color: white;
    padding: 8px 20px;
    text-align: center;
    text-decoration: none;
    display: inline-block;
    font-size: 16px;
}

.input {
    width: 70%;
    background: #f4f4f4;
    border: none;
}

#vue-spech {
    display: none;
}

.paraf {
    overflow-y: scroll;
    font-size: .9rem;
    text-align: justify;
}

.contextParaf {
    padding: 20px;
    font-size: 1.5rem;
    color: #16a085;
}

.color {
    background-color: #f4f4f4;
}

.white {
    color: #f4f4f4;
}

.flex {
    display: flex;
    flex-flow: row nowrap;
}

.left,
.right {
    background: #2d3436;
    height: 30rem;
    margin-top: 20px;
    width: 50% !important;
}

.right {
    background: #ecf0f1;
}

.container {
    width: 100%;
    height: auto;
}

.box {
    width: 100%;
    height: 100vh;
}

.jumbo {
    line-height: 1;
    margin-top: 0rem;
    font-weight: 200;
    color: #562f72;
    font-size: 2.25rem;
    padding-bottom: 20px;
}

.desc {
    font-weight: 300;
    display: block;
    color: #121212;
    font-size: 1rem;
}
</style>

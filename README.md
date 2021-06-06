<!-- PROJECT -->
<br />
  <h3 align="center">Personal Assistant</h3>
</p>


<!-- TABLE OF CONTENTS -->
<details open="open">
  <summary>Table of Contents</summary>
  <ol>
    <li>
      <a href="#about-the-project">About The Project</a>
      <ul>
        <li><a href="#built-with">Built With</a></li>
      </ul>
    </li>
    <li>
      <a href="#getting-started">Getting Started</a>
      <ul>
        <li><a href="#prerequisites">Prerequisites</a></li>
        <li><a href="#installation">Installation</a></li>
      </ul>
    </li>
    <li><a href="#usage">Usage</a></li>
    <li><a href="#contributing">Contributing</a></li>
    <li><a href="#license">License</a></li>
    <li><a href="#contact">Contact</a></li>
  </ol>
</details>



<!-- ABOUT THE PROJECT -->
## About The Project

[![Product Name Screen Shot][product-screenshot]](https://github.com/APPIAHTECH/PersonalAssistant/blob/main/images/screenshot.PNG)

This is a small version of Cortana. A personal assistant system. Given a reference context text (paragraph) and a question it returns the answer within the paragraph. The bot can only respond to economic inequality questions. This can be scaled by given more references, therefore the bot can have more knowledge about many topics, hence can respond to much more questions.

Example: 

Paragraph = "A study by the World Institute for Development Economics Research at United Nations University reports that the richest 1% of adults alone owned 40% of global assets in the year 2000. The three richest people in the world possess more financial assets than the lowest 48 nations combined. "

Question = What percentage of global assets does the richest 1% of people have?

Answer = 40%

### Built With

These are the technologies that are used.<br>
Server:
* [Flask](https://flask.palletsprojects.com/en/2.0.x/)<br>
Client :
* [Vuejs](https://vuejs.org/)<br>
Utils:
* [GoogleColab](https://research.google.com/colaboratory/)<br>

Model: Fine-Tuned BERT, from the transformers library
* [BERT](https://huggingface.co/transformers/pretrained_models.html)<br>

Dataset: Economic Inequality
* [EconomicInequality](https://rajpurkar.github.io/SQuAD-explorer/explore/1.1/dev/Economic_inequality.html?model=r-net+%20(ensemble)%20(Microsoft%20Research%20Asia)&version=1.1)<br>

Voice: TTS
* [SpeechSynthesisUtterance](https://developer.mozilla.org/en-US/docs/Web/API/SpeechSynthesisUtterance)<br>

Speech Recognition: STT
* [SpeechRecognition](https://developer.mozilla.org/en-US/docs/Web/API/SpeechRecognition)<br>

<!-- GETTING STARTED -->
## Getting Started

### Prerequisites

NPM is the recommended installation method when building large scale applications with Vue. It pairs nicely with module bundlers such as Webpack or Browserify. Vue also provides accompanying tools for authoring Single File Components.
* [Nodejs](https://nodejs.org/en/)

### Installation

#### install deps
1. ```sh
    npm install
    ``` 

#### serve examples at localhost:8080
2. ```sh
    npm run serve
    ``` 
#### Acces to GoogleColab
3. [GoogleColab](https://colab.research.google.com/drive/1Lq2Gf06-kiwb4XSBYCyLTnojRBad5cVZ?usp=sharing)

<!-- USAGE EXAMPLES -->
## Usage

To run the project.

#### Note run all section "Installation Setup", "Question Answering with a Fine-Tuned BERT", "Flask Server"
1. Run the google colab project. That will generate a server link. The link will be used to communicate with the client and serve. Each link is different, you will have something like: http://b4b8cf7e0cdd.ngrok.io

2. Copy the URL hostname. For instance b4b8cf7e0cdd
3. Open your project folder. Go to src/components. Open Karen.vue.
4. Change path and path_abs URL hostname with yours. For instance b4b8cf7e0cdd (remember yours is different)<br>
const path = 'http://b4b8cf7e0cdd.ngrok.io/api/question';<br>
const path_abs = 'http://b4b8cf7e0cdd.ngrok.io/api/abstract';

5. We are set and ready to go!. Init client, usually listen at http://localhost:8080/
* Run
  ```sh
  npm run serve
  ``` 

6. Talk or write your questions. Have fun!.

<!-- CONTRIBUTING -->
## Contributing

Contributions are what makes the open-source community such an amazing place to learn, inspire, and create. Any contributions you make are **greatly appreciated**.

1. Fork the Project
2. Create your Feature Branch (`git checkout -b feature/AmazingFeature`)
3. Commit your Changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the Branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request



<!-- LICENSE -->
## License

Distributed under the MIT License. See `LICENSE` for more information.


<!-- CONTACT -->
## Contact

Stephen Appiah- [@linkedin](https://www.linkedin.com/in/stephenappiahtech/) - stephenappiahtech@gmail.com

Project Link: [https://github.com/APPIAHTECH/PersonalAssistant](https://github.com/APPIAHTECH/PersonalAssistant)

<!-- ACKNOWLEDGEMENTS -->
## Acknowledgements
* [ChrisMcCormickAI](Applying BERT to Question Answering (SQuAD v1.1))



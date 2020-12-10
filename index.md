## **Bienvenido a la pagina de Logica Matematicas** 
Evelyn Zambrano
## **Este proyecto fue posible gracias  a las redes neuronales**.
  <img src="https://sites.google.com/site/mayinteligenciartificial/_/rsrc/1470337417111/unidad-4-redes-neuronales/3.jpg">
## *Que son las redes neuronales*.
son sistemas computacionales, inspirados en las neuronas que constituyen el cerebro de los animales, dotando a los ordenadores de inteligencia artificial. Están formadas por unidades básicas llamadas neuronas que se conectan entre sí formando la red neuronal.

<iframe width="560" height="315" src="https://www.youtube.com/embed/6vwfT3-mBBw?controls=0" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

## **Clasificación de redes neuronales artificiales**
     -Red neuronal Multicapa
     -Red neuronal Convolucional(CNN)
     -Red neuronal recurrente (RNN)
     -Redes de base radial (RBF)
     
##  *Red neuronal Multicapa*
   
 <img src="https://www.diegocalvo.es/wp-content/uploads/2017/07/perceptron-multicapa.png">
 
 es una generalización de la red neuronal monocapa, la diferencia reside en que mientras la red neuronal monocapa está compuesta por una capa de neuronas de entrada y una capa de neuronas de salida, esta dispone de un conjunto de capas intermedias (capas ocultas) entre la capa de entrada y la de salida.
 
##  *Red neuronal Convolucional (CNN)
 
 <img src="https://www.diegocalvo.es/wp-content/uploads/2017/07/red-neuronal-convolucional-arquitectura.png">

La principal diferencia de la red neuronal convolucional con el perceptrón multicapa viene en que cada neurona no se une con todas y cada una de las capas siguientes sino que solo con un subgrupo de ellas (se especializa).

##  *Red neuronal Recurrente(RNN)* 
 
  <img src="https://www.diegocalvo.es/wp-content/uploads/2017/07/red-neuronal-recurrente.png">

Las redes neuronales recurrentes no tienen una estructura de capas, sino que permiten conexiones arbitrarias entre las neuronas, incluso pudiendo crear ciclos, con esto se consigue crear la temporalidad, permitiendo que la red tenga memoria.

##  *Redes de base radial(RBF)*
  
  <img src="https://www.diegocalvo.es/wp-content/uploads/2017/07/Redes-de-base-radial.png">

calculan la salida de la función en función de la distancia a un punto denominado centro. La salida es una combinación lineal de las funciones de activación radiales utilizadas por las neuronas individuales.
    
##  *Cuál es su relacion con la teoria de grafos*
Son uno de los componentes fundamentales de la analítica social, relaciones entre personas y más recientemente se han utilizado sus propiedades para incrementar la eficiencia en la lucha contra el blanqueo de capitales y el fraude bancario.
<img src="https://revistadigital.inesem.es/informatica-y-tics/files/2017/03/Sin-t%C3%ADtulo-1.png">













<script src="https://www.gstatic.com/dialogflow-console/fast/messenger/bootstrap.js?v=1"></script>
<df-messenger
  intent="WELCOME"
  chat-title="Agente-logica"
  agent-id="f370c5d3-d652-4f7c-a087-61e862969284"
  language-code="es"
></df-messenger>
<div>Teachable Machine Image Model</div>
<button type="button" onclick="init()">Start</button>
<div id="webcam-container"></div>
<div id="label-container"></div>
<script src="https://cdn.jsdelivr.net/npm/@tensorflow/tfjs@1.3.1/dist/tf.min.js"></script>
<script src="https://cdn.jsdelivr.net/npm/@teachablemachine/image@0.8/dist/teachablemachine-image.min.js"></script>
<script type="text/javascript">
    // More API functions here:
    // https://github.com/googlecreativelab/teachablemachine-community/tree/master/libraries/image

    // the link to your model provided by Teachable Machine export panel
    const URL = "https://teachablemachine.withgoogle.com/models/RH-TmfbY9/";

    let model, webcam, labelContainer, maxPredictions;

    // Load the image model and setup the webcam
    async function init() {
        const modelURL = URL + "model.json";
        const metadataURL = URL + "metadata.json";

        // load the model and metadata
        // Refer to tmImage.loadFromFiles() in the API to support files from a file picker
        // or files from your local hard drive
        // Note: the pose library adds "tmImage" object to your window (window.tmImage)
        model = await tmImage.load(modelURL, metadataURL);
        maxPredictions = model.getTotalClasses();

        // Convenience function to setup a webcam
        const flip = true; // whether to flip the webcam
        webcam = new tmImage.Webcam(200, 200, flip); // width, height, flip
        await webcam.setup(); // request access to the webcam
        await webcam.play();
        window.requestAnimationFrame(loop);

        // append elements to the DOM
        document.getElementById("webcam-container").appendChild(webcam.canvas);
        labelContainer = document.getElementById("label-container");
        for (let i = 0; i < maxPredictions; i++) { // and class labels
            labelContainer.appendChild(document.createElement("div"));
        }
    }

    async function loop() {
        webcam.update(); // update the webcam frame
        await predict();
        window.requestAnimationFrame(loop);
    }

    // run the webcam image through the image model
    async function predict() {
        // predict can take in an image, video or canvas html element
        const prediction = await model.predict(webcam.canvas);
        for (let i = 0; i < maxPredictions; i++) {
            const classPrediction =
                prediction[i].className + ": " + prediction[i].probability.toFixed(2);
            labelContainer.childNodes[i].innerHTML = classPrediction;
        }
    }
</script>




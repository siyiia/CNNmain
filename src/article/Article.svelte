<script>
  import HyperparameterView from "../detail-view/Hyperparameterview.svelte";
  import Youtube from "./Youtube.svelte";

  let softmaxEquation = `$$\\text{Softmax}(x_{i}) = \\frac{\\exp(x_i)}{\\sum_j \\exp(x_j)}$$`;
  let reluEquation = `$$\\text{ReLU}(x) = \\max(0,x)$$`;
 let currentPlayer;
</script>

<body>
  <div id="description">
    <h2>What is a Convolutional Neural Network?</h2>
    <p>
      A CNN is a neural network: an algorithm used to recognize patterns in data. Neural Networks in general are composed of a collection of neurons that are organized in layers, each with their own learnable weights and biases.
    </p>
  	<ol>
  		<li>A <strong>tensor</strong> can be thought of as an n-dimensional matrix.  In the CNN above, tensors will be 3-dimensional with the exception of the output layer.</li>
  		<li>A <strong>neuron</strong> can be thought of as a function that takes in multiple inputs and yields a single output.  The outputs of neurons are represented above as the <span style="color:#FF7577;">red</span> &rarr; <span style="color:#60A7D7;">blue</span> <strong>activation maps</strong>.</li>
  		<li>A <strong>layer</strong> is simply a collection of neurons with the same operation, including the same hyperparameters.</li>
  		<li><strong>Kernel weights and biases</strong>, while unique to each neuron, are tuned during the training phase, and allow the classifier to adapt to the problem and dataset provided.  They are encoded in the visualization with a <span style="color:#BC8435;">yellow</span> &rarr; <span style="color:#39988F;">green</span> diverging colorscale.  The specific values can be viewed in the <em>Interactive Formula View</em> by clicking a neuron or by hovering over the kernel/bias in the <em>Convolutional Elastic Explanation View</em>.</li>
  		<li>A CNN conveys a <strong>differentiable score function</strong>, which is represented as <strong>class scores</strong> in the visualization on the output layer.</li>
  	</ol> 
  	

    <section class="try-it-out">
      <div id = "hyper">
        <HyperparameterView/>
      </div>
      <div class="right-col">
        <h2><span>Try It out</span></h2>
        <p><strong>Padding</strong> is often necessary when the kernel extends beyond the activation map. Padding conserves data at the borders of activation maps, and it can help preserve the input's spatial size.</p>
        <p><strong>Kernel size</strong> often also referred to as filter size, refers to the dimensions of the sliding window over the input. Choosing this hyperparameter has a massive impact on the image classification task. </p>
        <p><strong>Stride</strong> indicates how many pixels the kernel should be shifted over at a time. As stride is decreased, more features are learned because more data is extracted.</p>
      </div>
    </section>

  
  <h4><span>Activation</span> Functions</h4>
    <h6 id="article-relu">ReLU</h6>
    <p>
      Neural networks are extremely prevalent in modern technology&mdash;because
      they are so accurate! The highest performing CNNs today consist of an
      absurd amount of layers, which are able to learn more and more features.
      Part of the reason these groundbreaking CNNs are able to achieve such <a
        href="https://arxiv.org/pdf/1512.03385.pdf"
        title="ResNet">tremendous accuracies</a
      >
      is because of their non-linearity.  Non-linearity is necessary to produce non-linear decision boundaries,
      so that the output cannot be written as a linear combination of the inputs.
      The ReLU activation function is specifically used as
      a non-linear activation function, as opposed to other non-linear functions
      such as <em>Sigmoid</em> because it has been
      <a href="https://arxiv.org/pdf/1906.01975.pdf" title="See page 29"
        >empirically observed</a
      > that CNNs using ReLU are faster to train than their counterparts.
    </p>
    <p>
      The ReLU activation function is a one-to-one mathematical operation: {reluEquation}
    </p>
<!-- 
    <div class="rexFigg">
    <img
    src="PUBLIC_URL/assets/figures/relu_graph.png"
    alt="relu graph"
    width="40%"
    height="40%"
  />
  <div class="figure-caption">
    Figure 4. The ReLU activation function graphed, which disregards all
    negative data.
  </div>
</div>  -->

    <p>
      This activation function is applied elementwise on every value from the
      input tensor. You can observe how this
      activation function is applied by clicking a ReLU neuron in the network
      above. The Rectified Linear Activation function (ReLU) is performed after
      every convolutional layer in the network architecture outlined above.
      Notice the impact this layer has on the activation map of various neurons
      throughout the network!
    </p>
     <h6 id="article-softmax">Softmax</h6>
    <p>
      {softmaxEquation}
      A softmax operation serves a key purpose: making sure the CNN outputs sum to
      1. Because of this, softmax operations are useful to scale model outputs into
      probabilities. Clicking on the last layer reveals the softmax operation in
      the network. Notice how the logits after flatten aren’t scaled between zero
      to one. For a visual indication of the impact of each logit (unscaled scalar
      value), they are encoded using a
      <span style="color:#FFC385;">light orange</span>
      &rarr; <span style="color:#C44103;">dark orange</span> color scale. After passing
      through the softmax function, each class now corresponds to an appropriate
      probability!
    </p>
    <p>
      You might be thinking what the difference between standard normalization
      and softmax is&mdash;after all, both rescale the logits between 0 and 1.
      By using softmax, we are effectively “approximating” argmax while gaining
      differentiability. Rescaling doesn’t weigh the max significantly higher
      than other logits, whereas softmax does. 
    </p> 
  

   
    <section class = "explain">
      <div class="figure">
        <img
          src="PUBLIC_URL/assets/figures/convlayer_overview_demo.gif"
          alt="clicking on topmost first conv. layer activation map"
          width="60%"
          height="60%"
          align= "top"
        />
        <div class="figure-caption">
          Figure 1. As you hover over the activation map of the topmost node from
          the first convolutional layer, you can see that 3 kernels were applied
          to yield this activation map. After clicking this activation map, you
          can see the convolution operation occuring with each unique kernel.
        </div>
      </div>
    
  
      <div class="figure">
        <img
          src="PUBLIC_URL/assets/figures/convlayer_detailedview_demo.gif"
          alt="clicking on topmost first conv. layer activation map"
          width="80%"
          height="80%"
          align = "bottom"
        />
        <div class="figure-caption">
          Figure 2. The kernel being applied to yield the topmost intermediate
          result for the discussed activation map.
        </div>
  
          <img
            src="PUBLIC_URL/assets/figures/softmax_animation.gif"
            alt="softmax interactive formula view"
           
          />
          <div class="figure-caption">
            Figure 3. The <em>Softmax Interactive Formula View</em> allows a user to
            interact with both the color encoded logits and formula to understand how
            the prediction scores after the flatten layer are normalized to yield classification
            scores.
          </div>
        </div>
    </section>

  
  </div>
</body>

<style>
section.try-it-out{
    display: grid;
    grid-template-columns: repeat(2,50%);
    grid-template-areas: "CNN content";
    /* margin-left:35px;
    margin-right:15px; */
}

/*Hyperparameter view, margin*/
#hyper{
  margin-bottom: 60px;
  margin-top: 85px;
    margin-left: -25px;
    margin-right: -15px;
    grid-area: auto;
    text-align: auto;
    align-self: auto;
}

/*TRY IT OUT, margin*/
.right-col{
  margin-left: 35px;
    margin-right: 10px;
}


  #description {
    margin-bottom: 60px;
    margin-left: 60px;
    margin-right: 60px;
    /* max-width: 120ch; */
  }

  #description h2 {
    color: #444;
    font-size: 32px;
    font-weight: 450;
    margin-bottom: 12px;
    margin-top: 60px;
  }

  #description h4 {
    color: #444;
    font-size: 32px;
    font-weight: 450;
    margin-bottom: 8px;
    margin-top: 44px;
  }

  #description h6 {
    color: #444;
    font-size: 24px;
    font-weight: 450;
    margin-bottom: 8px;
    margin-top: 44px;
  }

  #description p {
    margin: 16px 0;
  }

  #description p img {

    vertical-align: middle;
  }

  #description .figure-caption {
    font-size: 15px;
    margin-top: 15px;
    margin-bottom: 15px;
  }
  

  #description ol {
    margin-left: 40px;
  }


  section.explain{
    display: grid;
    grid-template-columns: repeat(2,50%);
}

.img{
    margin-top: 20px;
    grid-area: CNN;
}

  h2{
    text-transform: uppercase;
    position: relative;
}

h2::before{
    content: ' ';
    position: absolute;
    width: 2.5em;
    background: #00bfff;
    height: .4em;
    bottom: 0;
    z-index: -1;
    margin-left: -.3em;
}

h4{
    text-transform: uppercase;
    position: relative;
}

h4::before{
    content: ' ';
    position: absolute;
    width: 2.5em;
    background: #00bfff;
    height: .4em;
    bottom: 0;
    z-index: -1;
    margin-left: -.3em;
}

  #description p,
  #description div,
  #description li {
    color: #555;
    font-size: 17px;
    line-height: 1.6;
  }

  #description small {
    font-size: 12px;
  }

  #description ol li img {
    vertical-align: middle;
  }

  #description .video-link {
    color: #3273dc;
    cursor: pointer;
    font-weight: normal;
    text-decoration: none;
  }

  #description ul {
    list-style-type: disc;
    margin-top: -10px;
    margin-left: 40px;
    margin-bottom: 15px;
  }

  #description a:hover,
  #description .video-link:hover {
    text-decoration: underline;
  }

  .figure{
    margin-top: auto;
    margin-left: AUTO;
    margin-right: auto;
    align-content: auto;

  }

  /*像素问题*/
  #description .rexFigg{
    margin-left: 400px;
    /* align-items: center; */
  }

  .video {
    width: 100%;
    display: flex;
    flex-direction: column;
    align-items: center;
  }
</style>

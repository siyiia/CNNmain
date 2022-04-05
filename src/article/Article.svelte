<script>
  import HyperparameterView from "../detail-view/Hyperparameterview.svelte";
  import Youtube from "./Youtube.svelte";

  let softmaxEquation = `$$\\text{Softmax}(x_{i}) = \\frac{\\exp(x_i)}{\\sum_j \\exp(x_j)}$$`;
  let reluEquation = `$$\\text{ReLU}(x) = \\max(0,x)$$`;

  let currentPlayer;
</script>

<body>
  <div id="description">
  <h2>Interactive features</h2>
  <ol>
    <li>
      <strong>Upload your own image</strong> by selecting
      <img
        class="icon is-rounded"
        src="PUBLIC_URL/assets/figures/upload_image_icon.png"
        alt="upload image icon"
        width="12%"
        height="12%"
      /> to understand how your image is classified into the 10 classes. By analyzing
      the neurons throughout the network, you can understand the activations maps
      and extracted features.
    </li>
    <li>
      <strong>Change the activation map colorscale</strong> to better
      understand the impact of activations at different levels of abstraction
      by adjusting
      <img
        class="is-rounded"
        width="9%"
        height="9%"
        src="PUBLIC_URL/assets/figures/heatmap_scale.png"
        alt="heatmap"
      />.
    </li>
    <li>
      <strong>Understand network details</strong> such as layer dimensions and
      colorscales by clicking the
      <img
        class="is-rounded"
        width="10%"
        height="10%"
        src="PUBLIC_URL/assets/figures/network_details.png"
        alt="network details icon"
      /> icon.
    </li>
    <li>
      <strong>Simulate network operations</strong> by clicking the
      <img
        class="icon is-rounded"
        src="PUBLIC_URL/assets/figures/play_button.png"
        alt="play icon"
        width="12%"
        height="12%"
      />
      button or interact with the layer slice in the
      <em>Interactive Formula View</em> by hovering over portions of the input
      or output to understand the mappings and underlying operations.
    </li>
    <li>
      <strong>Learn layer functions</strong> by clicking
      <img
        class="icon is-rounded"
        src="PUBLIC_URL/assets/figures/info_button.png"
        alt="info icon"
        width="12%"
        height="12%"
      />
      from the <em>Interactive Formula View</em> to read layer details from the
      article.
    </li>
  </ol>

  
  <section class = "explain">
    <div class="figure">
      <img
        src="PUBLIC_URL/assets/figures/convlayer_overview_demo.gif"
        alt="clicking on topmost first conv. layer activation map"
        width="60%"
        height="60%"
        align= "bottom"
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
    <!-- <h6>Understanding Hyperparameters</h6>
    <p>
      <HyperparameterView />
    </p> 

    <ol>
      <li>
        <strong>Padding</strong> is often necessary when the kernel extends
        beyond the activation map. Padding conserves data at the borders of
        activation maps, which leads to better performance, and it can help
        <a href="https://arxiv.org/pdf/1603.07285.pdf" title="See page 13"
          >preserve the input's spatial size</a
        >, which allows an architecture designer to build depper, higher
        performing networks. There exist
        <a
          href="https://arxiv.org/pdf/1811.11718.pdf"
          title="Outlines major padding techniques">many padding techniques</a
        >, but the most commonly used approach is zero-padding because of its
        performance, simplicity, and computational efficiency. The technique
        involves adding zeros symmetrically around the edges of an input. This
        approach is adopted by many high-performing CNNs such as
        <a
          href="https://papers.nips.cc/paper/4824-imagenet-classification-with-deep-convolutional-neural-networks.pdf"
          title="AlexNet">AlexNet</a
        >.
      </li>
      <li>
        <strong>Kernel size</strong>, often also referred to as filter size,
        refers to the dimensions of the sliding window over the input. Choosing
        this hyperparameter has a massive impact on the image classification
        task. For example, small kernel sizes are able to extract a much larger
        amount of information containing highly local features from the input.
        As you can see on the visualization above, a smaller kernel size also
        leads to a smaller reduction in layer dimensions, which allows for a
        deeper architecture. Conversely, a large kernel size extracts less
        information, which leads to a faster reduction in layer dimensions,
        often leading to worse performance. Large kernels are better suited to
        extract features that are larger. At the end of the day, choosing an
        appropriate kernel size will be dependent on your task and dataset, but
        generally, smaller kernel sizes lead to better performance for the image
        classification task because an architecture designer is able to stack
        <a
          href="https://arxiv.org/pdf/1409.1556.pdf"
          title="Learn why deeper networks perform better!"
          >more and more layers together to learn more and more complex features</a
        >!
      </li>
      <li>
        <strong>Stride</strong> indicates how many pixels the kernel should be shifted
        over at a time. For example, as described in the convolutional layer example
        above, Tiny VGG uses a stride of 1 for its convolutional layers, which means
        that the dot product is performed on a 3x3 window of the input to yield an
        output value, then is shifted to the right by one pixel for every subsequent
        operation. The impact stride has on a CNN is similar to kernel size. As stride
        is decreased, more features are learned because more data is extracted, which
        also leads to larger output layers. On the contrary, as stride is increased,
        this leads to more limited feature extraction and smaller output layer dimensions.
        One responsibility of the architecture designer is to ensure that the kernel
        slides across the input symmetrically when implementing a CNN. Use the hyperparameter
        visualization above to alter stride on various input/kernel dimensions to
        understand this constraint!
      </li>
    </ol> -->

    <section class="try-it-out">
      <div id = "hyper">
        <HyperparameterView/>
      </div>
      <div class="right-col">
        <h2><span>Try it out</span></h2>
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
      is because of their non-linearity. ReLU applies much-needed non-linearity into
      the model. Non-linearity is necessary to produce non-linear decision boundaries,
      so that the output cannot be written as a linear combination of the inputs.
      If a non-linear activation function was not present, deep CNN architectures
      would devolve into a single, equivalent convolutional layer, which would not
      perform nearly as well. The ReLU activation function is specifically used as
      a non-linear activation function, as opposed to other non-linear functions
      such as <em>Sigmoid</em> because it has been
      <a href="https://arxiv.org/pdf/1906.01975.pdf" title="See page 29"
        >empirically observed</a
      > that CNNs using ReLU are faster to train than their counterparts.
    </p>
    <p>
      The ReLU activation function is a one-to-one mathematical operation: {reluEquation}
    </p>

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
</div>

    <p>
      This activation function is applied elementwise on every value from the
      input tensor. For example, if applied ReLU on the value 2.24, the result
      would be 2.24, since 2.24 is larger than 0. You can observe how this
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
      Remember that backpropagation is a key aspect of training neural
      networks&mdash;we want the correct answer to have the largest “signal.” By
      using softmax, we are effectively “approximating” argmax while gaining
      differentiability. Rescaling doesn’t weigh the max significantly higher
      than other logits, whereas softmax does. Simply put, softmax is a “softer”
      argmax&mdash;see what we did there?
    </p>
    <!-- <div class="figure">
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
    </div> -->

   

    <h2>Video Tutorial</h2>
    <ul>
     <!-- 一个小段 -->
      <li class="video-link" on:click={currentPlayer.play(0)}>
        Luci Testing
        <small>(0:00-0:22)</small>
      </li>

      <li class="video-link" on:click={currentPlayer.play(27)}>
        <em>Thank you, bye</em>
        <small>(0:27-0:37)</small>
      </li>

      <li class="video-link" on:click={currentPlayer.play(37)}>
        3/23 <em>CNN View</em>
        <small>(0:37-0:46)</small>
      </li>
      <li class="video-link" on:click={currentPlayer.play(46)}>
        Convolutional, ReLU, and Pooling <em>Interactive Formula Views</em>
        <small>(0:46-1:21)</small>
      </li>
      <li class="video-link" on:click={currentPlayer.play(82)}>
        Flatten <em>Elastic Explanation View</em>
        <small>(1:22-1:41)</small>
      </li>
      <li class="video-link" on:click={currentPlayer.play(101)}>
        Softmax <em>Interactive Formula View</em>
        <small>(1:41-2:02)</small>
      </li>
      <li class="video-link" on:click={currentPlayer.play(126)}>
        Engaging Learning Experience: Understanding Classification
        <small>(2:06-2:28)</small>
      </li>
      <li class="video-link" on:click={currentPlayer.play(149)}>
        Interactive Tutorial Article
        <small>(2:29-2:54)</small>
      </li>
    </ul>
    <div class="video">
      <Youtube
        videoId="dQw4w9WgXcQ" 
        playerId="demo_video"
        bind:this={currentPlayer}
      />
    </div>
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

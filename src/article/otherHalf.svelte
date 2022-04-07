<script>
import Youtube from "./Youtube.svelte";
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
            4/6 <em>Luci Exhausting</em>
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
            videoId="T_lC2O1oIew" 
            playerId="demo_video"
            bind:this={currentPlayer}
          />
        </div>
    </div>
</body>

<style>
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


      #description p img {    
        vertical-align: middle;
      }
  
      #description ol {
        margin-left: 40px;
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
    
    
   
    
      .video {
        width: 100%;
        display: flex;
        flex-direction: column;
        align-items: center;
      }
    </style>
<body>
    <div class="hero-bg">
      <section class="top">
        <header>
           <!-- svelte-ignore a11y-invalid-attribute -->
           <a href="https://student.csc.liv.ac.uk/~sgzzhu20/comp208/">Main</a>
          </header>

         <h1><span>AI INSIGHT</span> A new approach to learning image processing algorithms </h1>

         <p> This website allows you to learn image processing algorithms with an interactive platform. Brief explaination will be uploaded in this page. Uploading, commenting and liking other's work is allowed here. </p>  
      </section>
    </div>
</body>


<style>
  @import url('https://fonts.googleapis.com/css2?family=Montserrat:wght@200;400&family=Nanum+Gothic&display=swap');

/*Custom properties*/
:root{
    --leading:1.5em;
}


body{
    font-family: 'Montserrat', sans-serif;
    margin: 0;
}

.hero-bg{
    /* background-image: URL("PUBLIC_URL/assets/img/bg2.jpg");
    background: #307D99 url('PUBliC\assets\img\bg2.jpg');
     */
  
    background-image: url("https://1.cms.s81c.com/sites/default/files/2020-10-20/Learn%20Leadspace%201.jpg");
  
    background-size: cover;
    color: white;
    text-align: center;
    padding-bottom: 4em;
}

header{
    padding: 1em 0;
}

.hero-bg a{
    color:white;
    text-decoration: none;
    font-weight: bold;
    font-size: 1.2rem;/*Better to use rem on font*/
}

section{
    margin: 0 1em;
}

h1{
    font-size: 2.5rem;
    margin: 2em 0 1.2em;
}

h1 span{
    text-transform: uppercase;
    display: block;
    font-size: 1.4rem;
    position: relative; 
    z-index: 1;
}


h1 span::before{
    content: ' ';
    position: absolute;
    width: 3em;
    background: #2D7D98;
    height: .4em;
    bottom: 0;
    z-index: -1;
    margin-left: -.3em;
}
 



p{
    line-height:var(--leading);
}

@media(min-width: 730px){
    section{
        margin: 0 4em;
    }
  

}

@media(min-width: 930px){
    .hero-bg{
        text-align: left;
    }
    .hero-bg p{
       font-weight: bold;
       margin: 0 0 3em;
    }
    .hero-bg section{
        width: 65%;
    }

}





.hero-bg p {
    margin-bottom: 0;
  }



.top{
    animation : fadeIn 2s forwards; 
}

@keyframes fadeIn{
    from{
       opacity: 0;
       transform: translateY(-2em);

    }
    to{
        opacity:1;
        transform: translateY(0);
    }
}

</style>

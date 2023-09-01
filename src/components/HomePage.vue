<template>
    
    <div class="landing">
        
        <div class="main">
            
                    <!-- <div class="header">
                    <span>Home</span>
                    <span>Men' Category</span>
                        <span>Women' Category</span>
                        
                    </div> -->
                        <div style="text-align: center;">
                            <h1 style="font-size: 300%;">Welcome To Fashop</h1>
                            <p>We Serve your need in Fashion way</p>
                        </div>
                    <div class="recommendation-card">
                       <h3>Newcomer</h3>
                       <div class="list">

                           <div v-for="value in catalog.filter(c => c.id !== 1)" :key="value.id">
                            <a :href="'/view/'+ value.id" class="card"> 
                                <div class="card-img">
                                    <!-- <img src="" style="width: 150px; height: 200px;" alt=""> -->
                                    <img :src="value.image" :alt="value.title" style=" background-color: white; border-radius: 15px; padding: 0 20px;width: 150px; height: 200px;" >
                                </div>
                                <div class="card-body">
                                    <div class="card-header">
                                        <span style="background-color: black; padding: 2px 5px; border-radius: 15px; color:white; ">$ {{ value.price }}</span>
                                        <div style="background-color: black; padding: 2px 5px; border-radius: 15px; color:white; ">{{ value.category }}</div>
                                    </div>
                                    <div class="card-title">{{ value.title }}</div>
                                    <div class="card-desc">
                                        {{ value.description }}
                                    </div>
                                    
                                </div>
                                <div class>

                                </div>
                            </a>
                            
                        </div>
                       </div>
                    </div>
                </div>
                    
    </div>
</template>

<script>
export default {
  name: 'HomePage',
  data(){
    return {
        catalog: null
    }
  },
  mounted() {
    fetch('https://fakestoreapi.com/products?limit=4')
            .then(res =>res.json())
            .then(json => this.catalog = json)
            .then(err => console.log(err.message))
  }
}   
</script>

<style>
    
    .landing{
        display: flex;
        justify-content: center;
        align-items: center;
        width: 100%;
        height: 70%;
        background: url('../assets/blur.svg') no-repeat;
        background-size: cover;
        /* background-position: 0 calc(100% - 200px); */
        background-color: #FDE2FF;
        /* color: #C9CFD0; */
    }
    .main{
        position: relative;
        z-index: 10;
        margin: 10%;
        top: 15vh;
        /* height: 80%; */
        width: 100%;
        background-color: rgba(210, 210, 210, 0.3);
        -webkit-backdrop-filter: blur(5px);
        backdrop-filter: blur(5px);
        
        /* border: 0.3333px solid black; */
        border-radius: 3vh;
        /* border-color: hsl(0, 0%, 80%, 0.4); */
    }
    .header{
        
        color: #C9CFD0;
        margin: 10px;
        background-color: rgba(0, 0, 0, 0.1);
        -webkit-backdrop-filter: blur(5px);
        backdrop-filter: blur(5px);
        border-radius: 1vh;
        border: 0.3333px solid black;
        border-color:  hsl(0, 0%, 80%, 0.4);
        height: max-content;
        padding: 5px;
        font-weight: bolder;
        width: max-content;
    }

    .recommendation-card{
        /* background-color: rgb(51,65,71); */
        width: 90%;
        margin: 20px
    }

    .list{
        display: flex;
        justify-content: center;
        align-items: center;
        max-height: 400px;

    }
    
    .card{
        text-decoration: none;
        background-color: rgb(255, 255, 255);
        border-radius: 10px;
        padding: 10px;
        max-width: 200px;
        color: black;
        display: flex;
        flex-direction: column;
        align-items: center;
        margin: 10px;
    }
    .card:hover{
        background-color: rgb(255, 255, 255, .4);
        backdrop-filter: blur(8px);
    }
    .card-body .card-img{
        
        max-width: 150px;
        max-height: 200px;
    }
    .card-body .card-header{
        display: flex;
        justify-content: space-between;
        align-items: center;
        font-size: 15px;
    }

    .card-title {
        font-weight: bolder;
        font-size: 150%;
        display: -webkit-box;
   -webkit-line-clamp: 2; /* number of lines to show */
           line-clamp: 2; 
   -webkit-box-orient: vertical;
        overflow: hidden;
    }

    .card-desc{
        font-size: 80%;
        font-weight: medium;
        display: -webkit-box;
   -webkit-line-clamp: 3; /* number of lines to show */
           line-clamp: 3; 
   -webkit-box-orient: vertical;
        overflow: hidden;
        text-indent: 10px;
    }
    /* @media only screen and (max-width: 720px) {
    .main {
        margin: 50px;
    }
    } */

    @media only screen  and (max-width: 1000px){
        .list{
            flex-direction: column;
            /* height: calc(45% - 30px); */
            overflow: scroll;
            justify-content: start;
            scroll-snap-align: start;
            scroll-behavior: smooth;
            /* scroll-position: 0 (-400px); */
        }

        .display{
            flex-direction: column;
            
        }
        

        .display div img{
            max-width: 300px;
            max-height: 350px;
            align-items: start;
            
        }
        
        .main{
            position: absolute;
            display: flex;
            justify-content: center;
            align-items: center;
            margin: 50px;
        }

        
        
    }
</style>
<template>
  <div class="landing">
      <div class="main">
          <div class="display">
              <div style="margin: 10px; ">
                <img :src="produk.image" alt="" style="width: 400px; height: 450px; background-color: white; padding: 20px; border-radius: 15px;">
              </div>
              
            <div class="display-card">
              <div>
                <h1>{{ produk.title }}</h1>
              </div>
              <div class="flex" style="justify-content: space-between; margin: 5px;">
                <div>
                  {{ produk.category }}
              
                </div>
                <div style="font-weight: bolder; display: flex; align-items: center;">
                  <div>

                    {{ produk.rating.rate }} / 5.0 
                  </div>
                  <div style="width: 100px; background-color: white; height: 15px; margin: 5px; border-radius: 10px; border: 0.3333px solid black;">
                      <div :style="'width: '+ produk.rating.rate * 10 *2  +'%; background-color: blue; height: 15px; border-radius: 10px;'"></div>
                  </div>
                </div>
              </div>
              <br>
              <hr>
              <br>
              <div style="text-indent: 50px; margin: 10px;">
                {{ produk.description }}
              </div>
              <br>
              <hr>
              <br>
              <div>
                <h1>$ {{ produk.price }}</h1>
              </div>
              <div style="margin: 10px 20%; text-align: center;">
                <div>
                  <button class="blue">Add To Cart</button>
                </div>
                <div style="display: flex; justify-content: center; align-items: center; ">
                  <button class="btn" v-on:click.prevent="prevId" >Prev</button>
                  <button class="btn" v-on:click.prevent="nextId" >Next</button>
                </div>
              </div>
            </div>
          </div>
      </div>
  </div>
</template>

<script>


export default {
  name: 'ViewPage',
  data(){
    return {
        produk: null,
        id2 : 1
    }
  },mounted(){
    const id =  this.$route.params.id;
    
    // console.log(this.id2);
    if((id > 0 && id < 4 ) || ( id > 15 && id < 20) || typeof id == 'undefined'){
      this.init(id);
    }else{
      window.location="../unavailable";
    }
      
  },
  methods: {
    next() {
      fetch(`https://fakestoreapi.com/products/${this.id2}`)
        .then(res=>res.json())
        .then(json=> this.produk = json)
    },
    nextId(){
      let x = this.id2;
      if((x > 0 && x < 4 ) || ( x > 15 && x < 20) ){
        ++this.id2;
        this.next();
      }else{
        if(this.id2 == 4){this.id2 = 16}
        else if(x == 20){this.id2 = 1}
        this.next();
      }
    },
    prevId(){
      let x = this.id2;
      if((x > 1 && x < 5 ) || ( x > 15 && x < 21) ){
        --this.id2;
        this.next();
      }else{
        if(this.id2 == 1){this.id2 = 20}
        else if(this.id2 == 15){this.id2 = 4}
        this.next();
      }
    },
    init(id){
      if(typeof id !== 'undefined'){
        this.id2 = id;
        fetch(`https://fakestoreapi.com/products/${id}`)
        .then(res=>res.json())
        .then(json=> this.produk = json)
      }else{
        this.next()
      }
    },
    
  }
}
</script>


<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>

<style>
.display-card{
  display: flex;
  flex-direction: column;
  margin: 50px 50px;
}

.display{
  width: 100%;
  display: flex;
  justify-content: center;
  align-items: start;
}

.blue{
  background-color: rgb(52, 52, 254);
  color:rgb(255, 255, 255);
  border-radius: 5px;
  border: none;
  padding: 5px;
  margin: 4px;
  cursor: pointer;
  font-size: 20px;
  font-weight: bold;
  box-shadow: 2px;
  width: 100%;
}
.btn{
  background-color: rgb(155, 155, 155, 0.2);
  color:rgb(43, 43, 43);
  border-radius: 5px;
  border: none;
  padding: 5px;
  /* margin: 4px; */
  margin-left: 5px;
  margin-top: 5px;
  cursor: pointer;
  font-size: 20px;
  font-weight: bold;
  box-shadow: 2px;
  width: 90%;
  border: 0.3333px solid rgb(52, 52, 254);
        border-color:  hsl(0, 0%, 80%, 0.4);
        text-align: center;
}
.btn:hover{
  scale: 102%;
}



</style>

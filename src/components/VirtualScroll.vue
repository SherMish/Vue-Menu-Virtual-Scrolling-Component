<template>
    <div class="menu-container">
        <div v-if="!hasClicked">
            <button v-on:click="hasClicked=true" class="button-5" role="button"> Open Menu </button>
        </div>
        <div v-if="hasClicked">
            <ul v-on:scroll.passive="onScroll" id="array-rendering" >
                <li v-for="(item,index) in items" :key="item">
                    <h3 v-if="index <= maxItems">
                        {{item}}</h3>
                </li>
            </ul>
        </div>
    </div>
</template>

<script>
export default {
    name: 'virtual-scroll',
    props: {
        arr_prop: {
            type: []
        }
    },
    
    created: function() { 
        let i_to;
        this.arr_prop.length >= 20 ? i_to = 20 : i_to = this.arr_prop.length;
        for (let i=0; i<i_to; i++) {
            this.items.push(this.arr_prop[i])
        }
    },

  data() {
    return {
        hasClicked: false,
        maxItems: 20,
        items: [],
        }
    },

    methods: {
        onScroll({ target: { scrollTop, clientHeight, scrollHeight }}) {
            if (this.arr_prop.length != this.maxItems) { //got more items to render
                if (scrollTop + clientHeight >= scrollHeight-1) { //bottom

                    let i = this.maxItems; //first element to render next is this.arr_prop[maxItems]
                    let i_to;

                    //last element to render this.arr_prop[maxItems+20 - 1] or this.arr_prop[this.arr_prop.length - 1]
                    this.arr_prop.length >= this.maxItems+20 ? i_to=this.maxItems+20 : i_to = this.arr_prop.length
                    while (i < i_to) { //push the next elements to render 
                        this.items.push(this.arr_prop[i]);
                        i++
                    }
                this.maxItems = i_to;
                    
                }
            }
        }
    }
}
</script>

<style>

.button-5 { 
    color: #fff;
    font-weight: bold;
    align-items: center;
    background-clip: padding-box;
    background-color: darkorange;
    border: 1px solid transparent;
    border-radius: .25rem;
    box-sizing: border-box;
    cursor: pointer;
    justify-content: center;
    line-height: 1.25;
    min-height: 3rem;
    padding: calc(.875rem - 1px) calc(1.5rem - 1px);
    position: relative;
    transition: all 250ms;
    touch-action: manipulation; 
    vertical-align: baseline; width: auto; 
    
}

.button-5:hover, .button-5:focus {
    background-color: #fb8332;
    box-shadow: rgba(0, 0, 0, 0.1) 0 4px 12px; 
} 
.button-5:hover {
    transform: translateY(-1px); 
} 

.button-5:active {
    background-color: red;
    box-shadow: rgba(0, 0, 0, .06) 0 2px 4px;
    transform: translateY(0); 
}


.menu-container {
    font-family: monospace;
}

ul {
    width: 300px;
    height: 200px;
    overflow: auto;
    background: darkorange;
    list-style: none;
}

li {
  color: #fff;
  background: darkorange;
  display: block;
  padding: 0.5rem;
  position: relative;
  text-decoration: none;
  transition-duration: 0.5s;
}

li:hover,
li:focus-within {
  background: red;
  cursor: pointer;
}







</style>
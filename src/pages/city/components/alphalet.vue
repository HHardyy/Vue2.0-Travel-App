<template>
    <ul class="list">
        <li class="item" 
        :key="item"
        :ref="item"
        v-for="item of letters"
        @touchstart.prevent="handelTouchStart"
        @touchmove="handelTouchMove"
        @touchend="handelTouchEnd"
        @click="handelFunction"
        >{{item}}</li>
    </ul>
</template>
<script>
	export default {
		name:"alphalet",
        props:{
            cities:Object
        },
        data(){
            return {
                touchStatus:false,
                startY:0,
                timer:null
            }
        },
        updated(){
            this.startY=this.$refs['A'][0].offsetTop
        },
        computed:{
            letters(){
                const letters=[]
                for (let i in this.cities) {
                    letters.push(i)
                }
                return letters 
            }
        },
        methods:{
            handelFunction(e){
                this.$emit("change",e.target.innerText)
            },
            handelTouchStart(){
                this.touchStatus=true
            },
            handelTouchMove(e){
                if (this.touchStatus) {
                    if (this.timer) {
                        clearTimeout(this.timer)
                    }
                    this.timer=setTimeout( ()=> {
                        const touchY=e.touches[0].clientY-79
                        const index=Math.floor((touchY-this.startY)/20)
                        if (index >= 0 && index <= this.letters.length) {
                            this.$emit("change",this.letters[index])
                        }
                    }, 16 )  
                } 
            },
            handelTouchEnd(){
                this.touchStatus=false
            }
        }
	}
</script>
<style lang="stylus" scoped>
   @import '~@/assets/styles/varyble.styl'
   .list
    position:absolute
    right:0
    top:1.58rem
    bottom:0
    width:.4rem
    display:flex
    flex-direction:column
    justify-content:center
    .item
     text-align:center
     line-height:.4rem
     color:$bgColor
</style>
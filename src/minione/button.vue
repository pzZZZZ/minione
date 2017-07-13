<template>
    <div>
        <button :class='btnClass' @click='changeColor'><slot>
    
        只有在没有要分发的内容时才会显示。
    
      </slot></button></div>
</template>
<script>
    export default {  
        data() {
            return {
                btnClass:"p-btn btn-primary blue"
            }
        },
        created(){
            if(this.type =='primary'){

            }else if(this.type ='ghost'){
                 this.btnClass ='p-btn btn-ghost blue '
            }
        },
        methods:{
            changeColor(){
                if(this.btnClass.includes('p-btn-clicked')){
                    return
                }
                let oldBtn = this.btnClass;
                this.btnClass=`p-btn btn-primary p-btn-clicked blue` ;
                setTimeout(()=>{
                this.btnClass=oldBtn ;
                },400)
            }
        },
        props: ["type"],
        watch: {
            type(val,oldval) {
                console.log(val) 
                if(val == 'ghost'){
                    // this.btnClass ='p-btn btn-ghost '
                }   
            }
        }
    }
</script>
<style lang="scss">
.p-btn{
     	position: relative;
	transition: all .3s;
	font-size: 14px;
	border-radius: 4px;
	background: transparent;
	padding: 4px 12px;
	cursor: pointer;
	text-decoration: none;
	font-family: Open Sans,Helvetica Neue,Helvetica,PingFang SC,Microsoft Yahei,WenQuanYi Micro Hei,\\5FAE\8F6F\96C5\9ED1,Arial,Verdana,sans-serif!important;
	outline: none;
	line-height: 1.42857143;
	text-align: center;
	white-space: nowrap;
	vertical-align: middle;
	-webkit-user-select: none;
	-moz-user-select: none;
	-ms-user-select: none;
	user-select: none
}
.btn-primary{
        border-style: solid;
    border-width: 1px;
    color: #fff;
    background: #108ee9;
    border-color: transparent;
}
.p-btn-clicked:after {
	content: "";
	transition: all .3s;
	position: absolute;
	left: -1px;
	right: -1px;
	top: -1px;
	bottom: -1px;
	z-index: 0;
	border: 0 solid #108ee9;
	opacity: .4;
	border-radius: inherit;
	display: block;
	animation: buttonEffect .36s ease-out forwards
}
.btn-ghost {
	border-style: solid;
	border-width: 1px
}
.btn-ghost.blue {
	border-color: #108ee9;
	color: #108ee9
}
.btn-primary:hover {
	background: #31a0f1
}

.btn-primary:active {
	background: #0d77c3
}
@keyframes buttonEffect {
	to {
		opacity: 0;
		top: -6px;
		left: -6px;
		bottom: -6px;
		right: -6px;
		border-width: 6px
	}
}
</style>

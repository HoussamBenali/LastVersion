<template>
    <div id="container">
         <div class="subcontainer">
        <div class="cambios bloque" >
            <h2><b>Avatar</b></h2>
            <hr>
            <div class="text-center izquierda">
                <div>
                    <img :src="'/api/getAvatar'" style="max-width: 100px; max-height: 100px; min-width: 100px; min-height: 100px" />
                    <hr>
                    <div class="cuadro_perfil">
                        <form @submit="formSubmit" enctype="multipart/form-data" >
                            <div class="form-group">
                                <strong class="change">Change it</strong>
                                <p></p>
                                <label class="btn btn-primary">
                                    <i class="fa fa-image"></i> Choose your file<input type="file" style="display: none;"  name="image" v-on:change="uploadImage"> 
                                </label>
                                <p :style="show">File: {{file}}</p>
                                
                                <!-- <input type="file" class="form-control" v-on:change="uploadImage" > -->
                            </div>
                            <button type="submit" class="">Send</button>
                        </form>
                    </div>
                </div>
            </div>
             </div>
        </div>
    </div>
</template>

<script>
import $ from 'jquery'
<<<<<<< HEAD
=======


>>>>>>> 889a5aeb852ccad9a961e7a68021eb3e9da9135a
export default {
    data() {
        return {
            image: '',
            success: '',
            img: null,
            file:'',
            show:{
                display: 'none'       
            }
        };
    },
<<<<<<< HEAD
=======

>>>>>>> 889a5aeb852ccad9a961e7a68021eb3e9da9135a
    methods: {
        uploadImage(e){
            //console.log(e.target.files[0],'hi');
            this.image = e.target.files[0];
            this.file = e.target.files[0].name
            this.show={display:'block'}
            //console.log(this.show)
        },
        async formSubmit(e) {
            e.preventDefault();
            let currentObj = this;
            const config = {
                headers: { 'content-type': 'multipart/form-data' }
            }
            let formData = new FormData();
            formData.append('image', this.image);
            await axios.post('api/updateAvatar', formData, config)
                .then(function (response) {
                    currentObj.success = response.data.success;
                    console.log(currentObj.success)
                }).catch(function (error) {
                    currentObj.output = error;
                });
            
            this.$router.go('changeAvatar');
        },
    },
<<<<<<< HEAD
=======

>>>>>>> 889a5aeb852ccad9a961e7a68021eb3e9da9135a
};
</script>
<style scoped>
.container{
    width: 100%;
    display: flex;
    align-items: center;
    justify-content: center;
    word-wrap: break-word;
}
<<<<<<< HEAD
=======

>>>>>>> 889a5aeb852ccad9a961e7a68021eb3e9da9135a
.subcontainer{
	margin-top: 0;
	display: flex;
	align-items: center;
	justify-content: center;
	width: 100%;
  }
 
  h2{
	margin-top:2vh;
    font-family: -apple-system,BlinkMacSystemFont,"Segoe UI",Roboto,"Helvetica Neue",Arial,"Noto Sans","Liberation Sans",sans-serif,"Apple Color Emoji","Segoe UI Emoji","Segoe UI Symbol","Noto Color Emoji";
  }
 
img{
    margin: 20px;
<<<<<<< HEAD
}
=======

}

>>>>>>> 889a5aeb852ccad9a961e7a68021eb3e9da9135a
.cuadro_perfil {
    display: flex;
    justify-content: center;
    align-items: center;
}

.izquierda {
    margin: 0!important;
    padding: 0!important;
    /*background-color:  #85c1e9;*/
}

.change {
    margin-bottom: 5vh;
    color: black;
    font-size: 20px;
    width: 100%;
    text-decoration: underline;
}
<<<<<<< HEAD
.underline{
    text-decoration: underline;
}
=======

.underline{
    text-decoration: underline;
}

>>>>>>> 889a5aeb852ccad9a961e7a68021eb3e9da9135a
.bloque{
    text-align: center;
    border:solid 3px black;
    border-radius: 1vh;
    min-width: 300px;
    padding: 2vh;
    padding-top: 0;
    margin-top: 3.5vh;
    margin-bottom: 3.5vh;
    width:40%;
    background-color: white;
}
<<<<<<< HEAD
=======



>>>>>>> 889a5aeb852ccad9a961e7a68021eb3e9da9135a
button {
	background-color: #4CAF50;
	border-radius: 1vh;
	color: white;
	padding: 1.5vh;
	margin: 8px 0;
	border: none;
	cursor: pointer;
	width: 100%;
  }
 
  button:hover {
	opacity: 0.8;
  }
<<<<<<< HEAD
</style>
=======
</style>
>>>>>>> 889a5aeb852ccad9a961e7a68021eb3e9da9135a

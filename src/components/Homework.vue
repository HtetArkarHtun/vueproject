<template>
<div>
		<h2 class="text-danger">Homework Component</h2>

	<div class="container">
      <div class="row">
        <div class="col-md-12">
          <div class="card mb-3" v-for="(datas,i) in info" :key="i">
            <div class="row no-gutters">
              <div class="col-md-4">
                <img :src="datas.item_photo" class="card-img" alt="...">
              </div>
              <div class="col-md-8">
                <div class="card-body">
                  <h5 class="card-title">{{datas.item_name}}</h5>
                  <p class="card-text">{{datas.item_codeno}}</p>
                  <p class="card-text">{{datas.item_price}}</p>

                  <p class="card-text">{{datas.item_description}}</p>
                  <p class="card-text"><small class="text-muted">Last updated 3 mins ago</small></p>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
</div>
</template>


<script type="text/javascript">
	export default{
		name: 'Homework',
		data(){
		return{
			loading: true,
			error: false,
			info:null
		}
	},
	mounted(){
		this.getData();
	},
	methods:{
		getData(){
			this.$http.get('http://jetpackmall.htetarkarhtun.me/api/items')
				.then(res=>{
					console.log(res);
					this.info =res.data.data;
				})
				.catch(err=>{
					this.error=true;
					console.log(err);
				})
				.finally(()=>{
					this.loading=false;
				})
			}		
		}
	}
</script>

<style type="text/css"></style>
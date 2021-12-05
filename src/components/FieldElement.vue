<template>
   <div class="fieldElement"> {{ content }} </div>
</template>

<script>
export default {
   name: 'FieldElement',
   props: {
      content: String
   }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.fieldElement {
	background: #fff;
	border: 1px solid #000;
	float: left;
	font-size: 40px;
	line-height: 68px;
	width: 68px;
	height: 68px;
	text-align: center;
}
</style>

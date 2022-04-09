<template>
<div>
<div class="row">
  <div class="leftcolumn">
    <div class="card">
		<div class="cardImg">
			<div class="grid-item item1">
				<img src="https://cdn.pixabay.com/photo/2015/04/23/22/00/tree-736885__480.jpg" />
			</div>
			<div class="grid-item item2">
				<h3>Title Here</h3>
				<p><span class="fa fa-star checked"></span>
<span class="fa fa-star checked"></span>
<span class="fa fa-star checked"></span>
<span class="fa fa-star"></span>
<span class="fa fa-star"></span></p>
				<p>Some text about me in culpa qui officia deserunt mollit anim..</p>
			</div>
			<div class="grid-item item3">
				<button>Show Details</button>
			</div>
		</div>
		
		
		
		<div class="cardImg">
			<div class="grid-item item1">
				<img src="https://cdn.pixabay.com/photo/2015/04/23/22/00/tree-736885__480.jpg" />
			</div>
			<div class="grid-item item2">
				<h3>Title Here</h3>
				<p><span class="fa fa-star checked"></span>
<span class="fa fa-star checked"></span>
<span class="fa fa-star checked"></span>
<span class="fa fa-star"></span>
<span class="fa fa-star"></span></p>
				<p>Some text about me in culpa qui officia deserunt mollit anim..</p>
			</div>
			<div class="grid-item item3">
				<button>Show Details</button>
			</div>
		</div>
		<div class="cardImg">
			<div class="grid-item item1">
				<img src="https://cdn.pixabay.com/photo/2015/04/23/22/00/tree-736885__480.jpg" />
			</div>
			<div class="grid-item item2">
				<h3>Title Here</h3>
				<p><span class="fa fa-star checked"></span>
<span class="fa fa-star checked"></span>
<span class="fa fa-star checked"></span>
<span class="fa fa-star"></span>
<span class="fa fa-star"></span></p>
				<p>Some text about me in culpa qui officia deserunt mollit anim..</p>
			</div>
			<div class="grid-item item3">
				<button>Show Details</button>
			</div>
		</div>
		<p>Lorem Ipsum is simply dummy text of the printing and typesetting industry. Lorem Ipsum has been the industry's standard dummy text ever since the 1500s, when an unknown printer took a galley of type and scrambled it to make a type specimen book. It has survived not only five centuries, but also the leap into electronic typesetting, remaining essentially unchanged. It was popularised in the 1960s with the release of Letraset sheets containing Lorem Ipsum passages, and more recently with desktop publishing software like Aldus PageMaker including versions of Lorem Ipsum.</p>
		<p>Lorem Ipsum is simply dummy text of the printing and typesetting industry. Lorem Ipsum has been the industry's standard dummy text ever since the 1500s, when an unknown printer took a galley of type and scrambled it to make a type specimen book. It has survived not only five centuries, but also the leap into electronic typesetting, remaining essentially unchanged. It was popularised in the 1960s with the release of Letraset sheets containing Lorem Ipsum passages, and more recently with desktop publishing software like Aldus PageMaker including versions of Lorem Ipsum.</p>
    </div>

  </div>
  <div class="rightcolumn">
    <div class="card">
      <h2>Filter Box</h2>
      <h4>Filter by Name:</h4>
      <p><input type="text"/></p>
	  
	  <h2>Filter by rating</h2>
      <h4>Filter by Name:</h4>
      <p><span class="fa fa-star checked"></span>
<span class="fa fa-star"></span>
<span class="fa fa-star"></span>
<span class="fa fa-star"></span>
<span class="fa fa-star"></span></p>
<p><span class="fa fa-star checked"></span>
<span class="fa fa-star"></span>
<span class="fa fa-star"></span>
<span class="fa fa-star"></span>
</p>
<p><span class="fa fa-star checked"></span>
<span class="fa fa-star"></span>
<span class="fa fa-star"></span>

</p>
<p><span class="fa fa-star checked"></span>
<span class="fa fa-star"></span>
</p>
<p><span class="fa fa-star checked"></span>

</p>
    </div>

  </div>
</div>
</div>
</template>

<style scoped>
.checked {
  color: orange;
} 
		* {
  box-sizing: border-box;
}

/* Add a gray background color with some padding */
body {
  font-family: Arial;
  padding: 20px;
  background: #f1f1f1;
}

/* Header/Blog Title */
.header {

}

/* Create two unequal columns that floats next to each other */
/* Left column */
.leftcolumn {   
  float: right;
  width: 75%;
}

/* Right column */
.rightcolumn {
  float: left;
  width: 25%;
  padding-right: 20px;
}

/* Fake image */
.fakeimg {
  background-color: #aaa;
  width: 100%;
  padding: 20px;
}

/* Add a card effect for articles */
.card {
   background-color: white;
   padding: 20px;
   margin-top: 20px;
}

/* Clear floats after the columns */
.row:after {
  content: "";
  display: table;
  clear: both;
}

/* Footer */
.footer {
  padding: 20px;
  text-align: center;
  background: #ddd;
  margin-top: 20px;
}

/* Responsive layout - when the screen is less than 800px wide, make the two columns stack on top of each other instead of next to each other */
@media screen and (max-width: 800px) {
  .leftcolumn, .rightcolumn {   
    width: 100%;
    padding: 0;
  }
}

.header{background-color: #333; display:flex; justify-content: space-between;}
.header ul {
  list-style-type: none;
  margin: 0;
  padding: 0;
  overflow: hidden;
  
}

.header li {
  float: left;
}

li a {
  display: inline-block;
  color: white;
  text-align: center;
  padding: 14px 16px;
  text-decoration: none;
}

li a:hover {
  background-color: #111;
}

.active {
  background-color: red;
}

.logo{font-size:20px; color:white; display:inline-block; padding:10px 15px; text-decoration:none;}
	.card{}	
	.cardImg{border:solid 1px #ccc; padding:20px; display:grid; grid-template-columns: 1fr 6fr 1fr; gap:20px; align-items:center;}
	.cardImg img{max-width:200px;}
	
	.rightcolumn .card input{width:100%; padding:10px 15px;}
    </style>

</style>
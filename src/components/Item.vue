<template>
<div class="steam-list"  v-show="show">
	<section class="steam-list-item" v-for="item in items">
		<div class="man-picture">
			<img class="avatar-img" :src="item.member.avatar_mini">
		</div>
		<div class="summary">
			<div class="title" v-link="{ name: 'content',params: { id: item.id}}">{{item.title}}</div>
			<ul class="list-inline tags">
				<li class="tag" @click="getListByNode(item.node.id,item.node.title)">{{item.node.title}}</li>
				<span class="split">·</span>
			</ul>
			<ul class="list-inline user-info">
				<li class="author" v-link="{ name: 'user',params: { username: item.member.username}}">{{item.member.username}}</li>
				<span class="split">·</span>
				<li class="last-modify-time">{{item.last_modified | getLastTimeStr true}}回复</li>
			</ul>
		</div>
	</section>
</div>
</template>
<script>
	export default {
		name:"Item",

		props:['show'],

		data(){
			return {
				items:Object
			}
		},

		methods:{
			getListByNode(node_id,node_name){
				this.$parent.getListByNode(node_id,node_name)
			}
		}
	}
</script>
<style>
	.steam-list{
		margin-top: 10px;
	}
	.man-picture{
		padding: 5px;
		margin-right: 10px;
	}
	.list-inline{
		margin: 0;
		padding:0;
		display: table-cell;
	}
	.list-inline>li{
		padding: 0 5px;
		display: inline-block;
		cursor: pointer;
	}
	.steam-list-item{
		width: 100%;
		display: inline-flex;
		border-bottom: 1px solid #eee;
		padding: 5px 0;
	}
	.summary{
		overflow: auto;
		overflow-x: hidden;
	}
	.title{
		font-size: 17px;
		padding-left: 5px;
		cursor: pointer;
	}
	.author {
	    font-size: 13px;
	    color: #999;
	}

</style>

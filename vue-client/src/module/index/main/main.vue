<!--===============
第一页:常用网页，本站简述 
===============-->

<template>
	<div class="h-100">
		<b-row no-gutters class="px-2">
			<b-col cols=12 xl=5 class="mx-auto">
				
				<!--===============
					 轮播图
				===============-->
				<div v-if="!imgShow">
					<el-carousel :interval="4000" type="card" height="100px">
						<el-carousel-item v-for="(v,k) in carousel" :key="k" class="text-center">
							<el-image :src="v" fit="scale-down" class="rounded">
								<div slot="error" class="image-slot">
									<i class="el-icon-picture-outline"></i>
								</div>
							</el-image>
						</el-carousel-item>
					</el-carousel>
				</div>
				
				<div v-if="imgShow">
					<el-carousel :interval="4000" type="card" height="100px">
						<el-carousel-item class="text-center ">
							<el-image @error="imgLoad">
								<div slot="error" class="image-slot ">
									<i class="el-icon-picture-outline "></i>
								</div>
							</el-image>
						</el-carousel-item>
					</el-carousel>
				</div>
				
				<!--===============
					 常用工具 
				===============-->
				<div>
					<el-divider content-position="left">常用工具</el-divider>
					<div class="row no-gutters">
						<div class="col d-flex">
							<el-input maxlength="10" size="mini" v-model="md5" placeholder="请输入内容" clearable>
								<template slot="prepend">md5加密</template>
							</el-input>
							<el-button size="mini" @click="getMd5">提交</el-button>
						</div>
					</div>
				</div>
				
				<!-- ===============
					 个人理念 
				=============== -->
				<div>
					<el-divider content-position="left">个人理念</el-divider>
					<b-alert class="border-left-5 border-left my-bgcolor p-2 mb-2" v-if="n !== null" show v-for="(n,k) in motto" :key="k"
					 v-text="n"></b-alert>
				</div>
			</b-col>

			<b-col cols=12 xl=6>

				<!-- ===============
					   常用网页
				  ===============-->
				<b-alert show variant="light" class="blockquote-footer m-0">
					<span class="mdi mdi-near-me mr-2"></span>
					<span>常用网页</span>
				</b-alert>

				<b-row no-gutters cols=3>
					<b-col v-for="n in nav" :key="n.id" class="mb-3 text-center">
						<el-popover placement="top-start" :title="n.tipsTitle" trigger="hover" :content="n.tips">
							<el-button @click="push(`${n.href}`)" slot="reference" size=small class="my-button-link">
								<span :class="['mdi',`${n.icon}`,'px-1', 'my-color']"></span>
								<small class="ml-1" v-text="n.name"></small>
							</el-button>
						</el-popover>
					</b-col>
				</b-row>

				<!--===============
						Github
				===============-->
				<b-alert show variant="light" class="blockquote-footer m-0">
					<span class="mdi mdi-gitlab mr-2"></span>
					<span>Github</span>
				</b-alert>

				<div>
					<div class="card border-0 mb-2" v-for="i in github" :key="i.url">
						<b-row no-gutters>
							<b-col cols="6" sm=3 md=5 xl=4 class="pr-2">
								<div class="d-flex justify-content-center">
									<el-image :src="i.img" fit="scale-down"></el-image>
								</div>
							</b-col>

							<b-col cols="6">
								<div>
									<h6 class="font-weight-bold text-center m-0" v-text="i.title"></h6>
									<div class="px-2">
										<small class="text-muted" v-text="i.description"></small>

										<!--===============
										 	 复制下载功能
										 	===============-->
										<div class="d-flex justify-content-around">
											<span class="mx-2">
												<el-link target="_blank" slot="reference" :underline="false" type="primary" class="el-icon-view el-icon--right"
												 :href="i.address">访问</el-link>
											</span>
											<span class="mr-2">
												<el-link type="primary" :href="i.download" :underline="false">下载</el-link>
											</span>
											<span class="mx-2">
												<el-tooltip class="item" effect="light" content="复制克隆" placement="right">
													<el-button @click="gitCopy(i.url)" class="no-outline" size="mini" type="primary" icon="el-icon-mobile"
													 circle>
													</el-button>
												</el-tooltip>
											</span>
										</div>

									</div>
								</div>

							</b-col>
						</b-row>
					</div>

				</div>
			</b-col>
		</b-row>

	</div>
</template>

<script>
	import attr from '@/module/index/main/attr/main.js'
	export default attr
</script>

<style scoped>
	@import url("./css/main.css");
</style>

<template>
	<div class="landscape">
		<div class="container">
			<ul class="landscape-list">
				<li class="landscape-item" v-for="(item, index) in items" :key="item.index">
					<div class="item-title flex">
						<h2>{{item.title}}</h2>
						<p>{{item.subtitle}}</p>	
					</div>  
					<div class="item-text">
						<p v-html="item.text"></p>
					</div>
					<div class="item-img flex">
						<img :src="item.img1" alt="">
						<img :src="item.img2" alt="">
					</div>
				</li>
			</ul>
		</div> 
	</div>
</template>

<script>
export default {
	data(){
		return{
			items: [
				{
					title: '武夷山',
					subtitle: '（世界文化与自然双重遗产，国家5A级旅游景区）',
					text: '武夷山位于江西与福建西北部两省交界处，武夷山脉北段东南麓总面积999.75平方公里，是中国著名的风景旅游区和避暑胜地。属典型的丹霞地貌，是首批国家级重点风景名胜区之一。<br/>武夷山是三教名山。[自秦汉以来，武夷山就为羽流禅家栖息之地，留下了不少宫观、道院和庵堂故址。武夷山还曾是儒家学者倡道讲学之地。<br/>武夷山自然保护区，是地球同纬度地区保护最好、物种最丰富的生态系统  ，拥有2527种植物物种，近5000种野生动物。<br/>武夷山是世界文化与自然双重遗产、 世界生物圈保护区、全国重点文物保护单位（武夷山崖墓群）、国家重点风景名胜区、国家AAAAA级旅游景区、国家级自然保护区 、国家水利风景区、  国家生态旅游示范区、  全国文明风景旅游区示范点 。<br/>2016年8月3日，国家旅游局召开新闻发布会，严重警告福建武夷山风景区。 2017年7月9日，江西铅山武夷山成功列入世界文化与自然遗产地。',
					img1: 'https://wanbangoss.oss-cn-beijing.aliyuncs.com/youtang/static/img/old/china/lanscape-wys01.jpg',
					img2: 'https://wanbangoss.oss-cn-beijing.aliyuncs.com/youtang/static/img/old/china/lanscape-wys02.jpg'
				},
				{
					title: '土楼',
					subtitle: '（土楼建筑）',
					text: '土楼，是利用未经焙烧的按一定比例的沙质黏土和黏质沙土拌合而成的泥土，以夹墙板夯筑而成墙体（少数以土坯砖砌墙）、柱梁等构架全部采用木料的楼屋，简言之，就是以生土版筑墙作为承重系统的任何两层以上的房屋。根据《现代汉浯词典》的解释，所谓“楼”，就是“两层或两层以上的房子”。据此，一层的房子，即使以生土墙承重、以木料作为柱梁等构架，也不能称为土楼，只能称为土屋。土楼是世界独一无二的大型民居形式，被称为中国传统民居的瑰宝。<br/>土楼是分布在中国东南部的福建、江西、广东三省的客家地区，以生土为主要建筑材料、生土与木结构相结合，并不同程度地使用石材的大型居民建筑。它们是几次中国乃至东亚历史动荡和民众大迁徙的产物。其中分布最广、数量最多、品类最丰富、保存最完好的，是福建土楼。<br/>土楼已被严格确认的福建土楼建筑有3000余座，主要分布在福建省龙岩永定县、福建省漳州南靖县和华安县，其中又以客家土楼为代表。土楼的兴建高潮是在中国动乱与客家族群由中原向南方迁移之际。这些时期包含唐末黄巢之乱、南宋政权南移与明末清初。直至17世纪之后，不但让客家人最后定居于中国东南沿海，也让土楼分布地点以中国闽粤地区为大宗。出于抵御山林野兽、强盗的需要，并体现儒家思想下大家族共同生活的理想，乃建造此种形式特殊的建筑的。<br/>在民间俗语中，“土楼”亦是“土楼房”的简称，与“洋楼房”相对而言，泛指没有集中供暖和燃气管道的简易低层楼房。',
					img1: 'https://wanbangoss.oss-cn-beijing.aliyuncs.com/youtang/static/img/old/china/lanscape-tl01.jpg',
					img2: 'https://wanbangoss.oss-cn-beijing.aliyuncs.com/youtang/static/img/old/china/lanscape-tl02.jpg'
				},
				{
					title: '西湖',
					subtitle: '（浙江省杭州市西湖）',
					text: '西湖，位于浙江省杭州市西面，是中国大陆首批国家重点风景名胜区和中国十大风景名胜之一。它是中国大陆主要的观赏性淡水湖泊之一，也是现今《世界遗产名录》中少数几个和中国唯一一个湖泊类文化遗产。<br/>西湖三面环山，面积约6.39平方千米，东西宽约2.8千米，南北长约3.2千米，绕湖一周近15千米。湖中被孤山、白堤、苏堤、杨公堤分隔，按面积大小分别为外西湖、西里湖、北里湖、小南湖及岳湖等五片水面，苏堤、白堤越过湖面，小瀛洲、湖心亭、阮公墩三个小岛鼎立于外西湖湖心，夕照山的雷峰塔与宝石山的保俶塔隔湖相映，由此形成了“一山、二塔、三岛、三堤、五湖”的基本格局。',
					img1: 'https://wanbangoss.oss-cn-beijing.aliyuncs.com/youtang/static/img/old/china/lanscape-xh01.jpg',
					img2: 'https://wanbangoss.oss-cn-beijing.aliyuncs.com/youtang/static/img/old/china/lanscape-xh02.jpg'
				},
				{
					title: '乌镇',
					subtitle: '（浙江省嘉兴市桐乡市乌镇）',
					text: '乌镇，位于浙江省嘉兴市桐乡，地处江浙沪“金三角”之地、杭嘉湖平原腹地，距杭州、苏州均为60公里，距上海106公里。乌镇属太湖流域水系，河流纵横交织，京杭大运河依镇而过。乌镇原以市河为界，分为乌青二镇，河西为乌镇，属湖州府乌程县；河东为青镇，属嘉兴府桐乡县。解放后，市河以西的乌镇划归桐乡县，才统称乌镇。全镇辖13个社区居委会和18个行政村。陆上交通有贯穿镇区的县级公路姚震线，与省道盐湖公路、国道320公路、318公路、沪杭高速公路（申嘉湖高速）相衔接。<br/>乌镇是首批中国历史文化名镇、中国十大魅力名镇、全国环境优美乡镇、国家5A级景区，素有“中国最后的枕水人家”之誉，拥有7000多年文明史和1300年建镇史。  乌镇是典型的中国江南水乡古镇，有“鱼米之乡、丝绸之府”之称。乌镇具有六千余年悠久历史，是全国二十个黄金周预报景点及江南六大古镇之一。1991年被评为浙江省历史文化名城；2014年11月19日始，乌镇成为世界互联网大会永久会址。',
					img1: 'https://wanbangoss.oss-cn-beijing.aliyuncs.com/youtang/static/img/old/china/lanscape-wz01.jpg',
					img2: 'https://wanbangoss.oss-cn-beijing.aliyuncs.com/youtang/static/img/old/china/lanscape-wz02.jpg'
				},
				{
					title: '普陀山',
					subtitle: '（中国佛教四大名山之一）',
					text: '普陀山，与山西五台山、四川峨眉山、安徽九华山并称为中国佛教四大名山，是观世音菩萨教化众生的道场。普陀山是舟山群岛1390个岛屿中的一个小岛，形似苍龙卧海，面积近13平方公里，与舟山群岛的沈家门隔海相望，素有“海天佛国”、“南海圣境”之称，是首批国家重点风景名胜区。2007年（丁亥年）5月8日，舟山市普陀山风景名胜区，经国家旅游局正式批准，为国家5A级旅游风景区。“海上有仙山，山在虚无缥缈间”，普陀山以其神奇、神圣、神秘，成为驰誉中外的旅游胜地。普陀山是国务院首批公布的44个国家级重点风景名胜区之一，中国国家5A级旅游景区，全国文明山、卫生山，浙江省唯一的ISO14000国家示范区。',
					img1: 'https://wanbangoss.oss-cn-beijing.aliyuncs.com/youtang/static/img/old/china/lanscape-pts01.jpg',
					img2: 'https://wanbangoss.oss-cn-beijing.aliyuncs.com/youtang/static/img/old/china/lanscape-pts02.jpg'
				}
			]
		}
	}
}
</script>

<style lang="less" scoped>
	.landscape{ padding-bottom: 80px;
		.landscape-list{ 
			.landscape-item{ margin-top: 80px;
				.item-title{ color: #333;
					h2{ font-size: 32px;}
					p{ margin-top: 10px; margin-left: 5px; font-size: 20px;}
				}
				.item-text{ margin-top: 30px; color: #333;
					p{ font-size: 16px;}
				}
				.item-img{ margin-top: 30px;
					img{ margin-right: 60px; width: 570px; height: 400px; background-color: #eee;}
					img:nth-child(2){ margin-right: 0;}
				}
			}
		}
	}
</style>

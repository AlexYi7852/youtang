<template>
	<div class="story">
		<div class="container">
			<h1>历史故事</h1>
			<ul class="story-list">
				<li class="story-item" v-for="(item, index) in items" :key="item.index">
					<div class="item-title flex">
						<h2>{{item.title}}</h2>
					</div>
					<div class="item-text">
						<p v-html="item.text"></p>
					</div>
					<div class="item-img">
						<img :src="item.img" alt="">
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
					title: '1.八仙过海',
					text: '传说很久以前，有八位仙人要到东海的仙岛上去参加王母娘娘的生日宴会。但是东海龙王没有受到生日宴会的邀请，他非常生气，决定阻止八仙去参加宴会。当八仙来到东海边时，他们看到海面上巨浪惊人。 <br/>仙人们决定把自己的法宝放在水面上，站立在法宝上渡过大海。于是，铁拐李站在拐杖上，吕洞宾站在宝剑上；蓝采和坐在花篮里；张果老骑在毛驴上；曹国舅脚踏玉板；韩湘子骑在笛子上；汉钟离把芭蕉扇踩在脚下；何仙姑坐在莲花上。就这样，八位仙人迎着海上的狂风巨浪，衣带招展，奇迹般地渡过了东海。',
					img: 'https://wanbangoss.oss-cn-beijing.aliyuncs.com/youtang/static/img/old/china/story-bxgh.jpg',
				},
				{
					title: '2.司马光砸缸',
					text: '司马光七岁那年，有一天，他和小伙伴们在学校里玩儿。学校里有一口大水缸，有个小伙伴爬到缸上面去玩儿，一不小心，掉到了缸里。缸大水深，孩子很快就要沉下去了，大家都很着急。<br/>别的孩子一见出了事，都吓得又哭又叫，跑到外面向大人求救。司马光却急中生智，从地上捡起一块大石头，使劲向水缸砸去，“砰！”水缸破了，缸里的水流了出来，小孩得救了，小伙伴们都很高兴。<br/>这就是遇事沉着冷静的小司马光',
					img: 'https://wanbangoss.oss-cn-beijing.aliyuncs.com/youtang/static/img/old/china/story-smg.jpg',
				},
				{
					title: '3.郑和下西洋',
					text: '永乐四年(一四零六年)六月，郑和第一次下西洋，顺风南下，到达爪哇岛上的麻喏八歇国。爪哇古名阇婆，今印度尼西亚爪哇岛，为南洋要冲，人口稠密，物产丰富，商业发达。 <br/>当时，这个国家的东王、西王正在打内战。东王战败，其属地被西王的军队占领。郑和船队的人员上岸到集市上做生意，被占领军误认为是来援助东王的，被西王麻喏八歇王误杀，计一百七十人。郑和部下的军官纷纷请战，说将士的血不能白流，急于向麻喏八歇国进行宣战，给以报复。 <br/>“爪哇事件”发生后，西王十分惧怕，派使者谢罪，要赔偿六万两黄金以赎罪。郑和第一次下西洋就出师不利，而且又无辜损失了一百七十名将士，按常情必然会引发一场大规模战斗。然而，郑和得知这是一场误杀，又鉴于西王诚惶诚恐，请罪受罚，于是禀明皇朝，化干戈为玉帛，和平处理这一事件。明王朝决定放弃对麻喏八歇国的赔偿要求，西王知道这件事后，十分感动，两国从此和睦相处。 <br/>爪哇岛三宝垄纪念郑和六百周年活动组委会成员向记者谈及此事，都十分敬佩，说郑和对各国不论强弱亲疏，平等对待，一视同仁，即时两国发生冲突，仍能保持极大的克制，委曲求全，以理服人，表现出对邻国的和平共处，睦邻友好，使中国和印尼两国人民的传统友谊源远流长，我们定居在这里也感到脸上有光，我们以郑和为骄傲。 <br/>印尼的学者认为，郑和舰队是当时世界上最强大的海上特混舰队。而郑和七下西洋的二十八年中，真正意义上的对外战争仅有锡兰(今斯里兰卡)一次，而且是在被迫无奈的情况下的防卫性作战。郑和在处理“爪哇事件”中，不但不动用武力，而且不要赔偿，充分体现了郑和是传播和平的使者，他传播的是“以和为贵”的中国传统礼仪，以及“四海一家”、“天下为公”的中华文明。',
					img: 'https://wanbangoss.oss-cn-beijing.aliyuncs.com/youtang/static/img/old/china/story-zh.jpg',
				}
			]
		}
	}
}
</script>

<style lang="less" scoped>
	.story{ padding: 80px 0;
		h1{ text-align: center; font-size: 32px; color: #333;}
		.story-list{ margin-top: 30px;
			.story-item{ margin-bottom: 80px;
				.item-title{ color: #333;
					h2{ font-size: 24px;}
				}
				.item-text{ margin-top: 10px; color: #333;
					p{ font-size: 16px;}
				}
				.item-img{ margin-top: 30px;
					img{ width: 100%; height: 500px; background-color: #eee;}
				}
			}
		}
	}
</style>

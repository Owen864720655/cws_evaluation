## 中文分词器分词效果评估对比

### [捐赠致谢](https://github.com/ysc/QuestionAnsweringSystem/wiki/donation)

### 使用说明：

   如何建立开发环境？
   
	如果是使用Netbeans、IDEA，则直接打开项目
	如果是使用Eclipse、MyEclipse，则要执行导入操作
	推荐使用IDEA

   评估采用的测试文本位于data目录下，253 3709行，共2837 4490个字符
   
   test-test.txt为未分词的文件，一行一个句子或短语，格式如下：
   
	   迈向充满希望的新世纪
	   一九九八年新年讲话
	   附图片1张
	   中共中央总书记
	   国家主席江泽民
	   一九九七年十二月三十一日
	   12月31日
	   总书记
	   国家主席江泽民发表1998年新年讲话
	   新华社记者兰红光摄
	   
   standard-text.txt为人工分好词的文件，用于判断参与评估的分词器的分词结果是否正确，词和词之间以空格分隔，格式如下：
   
	   迈向 充满 希望 的 新 世纪
	   一九九八年 新年 讲话
	   附 图片 1 张
	   中共中央 总书记
	   国家 主席 江泽民
	   一九九七年 十二月 三十一日
	   12月 31日
	   总书记
	   国家 主席 江泽民 发表 1998年 新年 讲话
	   新华社 记者 兰红光 摄
	   
   speed-test-text.txt用于纯粹的速度对比
   
   注意：由于每个分词器的词典格式不一致，除了词典之外使用的其他模型的格式也不一致，所以我们评估对比时没有让所有分词器使用统一的词典和模型，测试的是各个分词器的默认行为
   
   运行org.apdplat.evaluation.Evaluator类可获得评估结果
   
   运行org.apdplat.evaluation.WordSegmenter类可对比不同分词器结果
   
   windows:
   
	   ./contrast.bat
	   ./evaluation.bat

   linux:
   
	   chmod +x contrast.sh & ./contrast.sh
	   chmod +x evaluation.sh & ./evaluation.sh

   最终评估结果文件位于report目录下：分词效果评估报告.txt

   注意：stanford分词器是吃内存的怪兽，运行的时候需要增加虚拟机参数 -Xms3000m -Xmx3000m
      	
### 评估报告：

    1、word分词 最大Ngram分值算法：
    分词速度：370.9714 字符/毫秒
    行数完美率：66.55%  行数错误率：33.44%  总的行数：2533709  完美行数：1686210  错误行数：847499
    字数完美率：60.94% 字数错误率：39.05% 总的字数：28374490 完美字数：17293964 错误字数：11080526
    
    2、word分词 最少词数算法：
    分词速度：330.1586 字符/毫秒
    行数完美率：65.67%  行数错误率：34.32%  总的行数：2533709  完美行数：1663958  错误行数：869751
    字数完美率：60.12% 字数错误率：39.87% 总的字数：28374490 完美字数：17059641 错误字数：11314849
    
    3、HanLP分词器 标准分词：
    分词速度：935.7724 字符/毫秒
    行数完美率：58.31%  行数错误率：41.68%  总的行数：2533709  完美行数：1477422  错误行数：1056287
    字数完美率：50.43% 字数错误率：49.56% 总的字数：28374490 完美字数：14311008 错误字数：14063482
    
    4、word分词 全切分算法：
    分词速度：62.960262 字符/毫秒
    行数完美率：57.2%  行数错误率：42.79%  总的行数：2533709  完美行数：1449288  错误行数：1084421
    字数完美率：47.95% 字数错误率：52.04% 总的字数：28374490 完美字数：13605742 错误字数：14768748
    
    5、Ansj BaseAnalysis 基本分词：
    分词速度：1295.5205 字符/毫秒
    行数完美率：55.36%  行数错误率：44.63%  总的行数：2533709  完美行数：1402905  错误行数：1130804
    字数完美率：48.18% 字数错误率：51.81% 总的字数：28374490 完美字数：13672441 错误字数：14702049
    
    6、smartcn：
    分词速度：611.1504 字符/毫秒
    行数完美率：55.29%  行数错误率：44.7%  总的行数：2533690  完美行数：1401069  错误行数：1132621
    字数完美率：48.03% 字数错误率：51.96% 总的字数：28374433 完美字数：13628910 错误字数：14745523
    
    7、Ansj ToAnalysis 精准分词：
    分词速度：759.40717 字符/毫秒
    行数完美率：54.72%  行数错误率：45.27%  总的行数：2533709  完美行数：1386683  错误行数：1147026
    字数完美率：44.99% 字数错误率：55.0% 总的字数：28374490 完美字数：12768426 错误字数：15606064
    
    8、HanLP分词器 极速词典分词：
    分词速度：6015.3677 字符/毫秒
    行数完美率：54.25%  行数错误率：45.74%  总的行数：2533709  完美行数：1374736  错误行数：1158973
    字数完美率：46.12% 字数错误率：53.87% 总的字数：28374490 完美字数：13088320 错误字数：15286170
    
    9、word分词 双向最大最小匹配算法：
    分词速度：462.87158 字符/毫秒
    行数完美率：53.06%  行数错误率：46.93%  总的行数：2533709  完美行数：1344624  错误行数：1189085
    字数完美率：43.07% 字数错误率：56.92% 总的字数：28374490 完美字数：12221610 错误字数：16152880
    
    10、HanLP分词器 N-最短路径分词：
    分词速度：77.89775 字符/毫秒
    行数完美率：53.01%  行数错误率：46.98%  总的行数：2533709  完美行数：1343252  错误行数：1190457
    字数完美率：44.42% 字数错误率：55.57% 总的字数：28374490 完美字数：12604878 错误字数：15769612
    
    11、HanLP分词器 最短路径分词：
    分词速度：384.70233 字符/毫秒
    行数完美率：52.94%  行数错误率：47.05%  总的行数：2533709  完美行数：1341450  错误行数：1192259
    字数完美率：43.76% 字数错误率：56.23% 总的字数：28374490 完美字数：12417741 错误字数：15956749
    
    12、Ansj NlpAnalysis NLP分词：
    分词速度：172.19516 字符/毫秒
    行数完美率：52.66%  行数错误率：47.33%  总的行数：2533709  完美行数：1334314  错误行数：1199395
    字数完美率：42.66% 字数错误率：57.33% 总的字数：28374490 完美字数：12105808 错误字数：16268682
    
    13、HanLP分词器 NLP分词：
    分词速度：408.2249 字符/毫秒
    行数完美率：52.18%  行数错误率：47.81%  总的行数：2533709  完美行数：1322216  错误行数：1211493
    字数完美率：43.03% 字数错误率：56.96% 总的字数：28374490 完美字数：12211399 错误字数：16163091
    
    14、FudanNLP：
    分词速度：123.456985 字符/毫秒
    行数完美率：51.48%  行数错误率：48.51%  总的行数：2533709  完美行数：1304371  错误行数：1229338
    字数完美率：43.22% 字数错误率：56.77% 总的字数：28374490 完美字数：12265742 错误字数：16108748
    
    15、Jieba SEARCH：
    分词速度：993.435 字符/毫秒
    行数完美率：50.84%  行数错误率：49.15%  总的行数：2533709  完美行数：1288237  错误行数：1245472
    字数完美率：41.54% 字数错误率：58.45% 总的字数：28374490 完美字数：11789036 错误字数：16585454
    
    16、Jcseg 复杂模式：
    分词速度：561.55975 字符/毫秒
    行数完美率：47.96%  行数错误率：52.03%  总的行数：2533709  完美行数：1215171  错误行数：1318538
    字数完美率：38.84% 字数错误率：61.15% 总的字数：28374490 完美字数：11021588 错误字数：17352902
    
    17、word分词 双向最小匹配算法：
    分词速度：967.68604 字符/毫秒
    行数完美率：46.34%  行数错误率：53.65%  总的行数：2533709  完美行数：1174276  错误行数：1359433
    字数完美率：36.07% 字数错误率：63.92% 总的字数：28374490 完美字数：10236574 错误字数：18137916
    
    18、word分词 双向最大匹配算法：
    分词速度：661.148 字符/毫秒
    行数完美率：46.18%  行数错误率：53.81%  总的行数：2533709  完美行数：1170075  错误行数：1363634
    字数完美率：35.65% 字数错误率：64.34% 总的字数：28374490 完美字数：10117122 错误字数：18257368
    
    19、HanLP分词器 索引分词：
    分词速度：942.4862 字符/毫秒
    行数完美率：45.44%  行数错误率：54.55%  总的行数：2533709  完美行数：1151473  错误行数：1382236
    字数完美率：35.48% 字数错误率：64.51% 总的字数：28374490 完美字数：10068062 错误字数：18306428
    
    20、Jcseg 简易模式：
    分词速度：1193.3085 字符/毫秒
    行数完美率：44.59%  行数错误率：55.4%  总的行数：2533709  完美行数：1130000  错误行数：1403709
    字数完美率：35.78% 字数错误率：64.21% 总的字数：28374490 完美字数：10155059 错误字数：18219431
    
    21、word分词 正向最大匹配算法：
    分词速度：1567.1318 字符/毫秒
    行数完美率：41.88%  行数错误率：58.11%  总的行数：2533709  完美行数：1061189  错误行数：1472520
    字数完美率：31.35% 字数错误率：68.64% 总的字数：28374490 完美字数：8896173 错误字数：19478317
    
    22、word分词 逆向最大匹配算法：
    分词速度：1232.6017 字符/毫秒
    行数完美率：41.69%  行数错误率：58.3%  总的行数：2533709  完美行数：1056515  错误行数：1477194
    字数完美率：30.98% 字数错误率：69.01% 总的字数：28374490 完美字数：8792532 错误字数：19581958
    
    23、word分词 逆向最小匹配算法：
    分词速度：1936.9575 字符/毫秒
    行数完美率：41.42%  行数错误率：58.57%  总的行数：2533709  完美行数：1049673  错误行数：1484036
    字数完美率：31.34% 字数错误率：68.65% 总的字数：28374490 完美字数：8893622 错误字数：19480868
    
    24、Ansj IndexAnalysis 面向索引的分词：
    分词速度：677.1308 字符/毫秒
    行数完美率：40.66%  行数错误率：59.33%  总的行数：2533709  完美行数：1030336  错误行数：1503373
    字数完美率：29.81% 字数错误率：70.18% 总的字数：28374490 完美字数：8459997 错误字数：19914493
    
    25、MMSeg4j ComplexSeg：
    分词速度：1699.5801 字符/毫秒
    行数完美率：38.81%  行数错误率：61.18%  总的行数：2533688  完美行数：983517  错误行数：1550171
    字数完美率：29.6% 字数错误率：70.39% 总的字数：28374428 完美字数：8400089 错误字数：19974339
    
    26、MMSeg4j SimpleSeg：
    分词速度：2355.5115 字符/毫秒
    行数完美率：37.57%  行数错误率：62.42%  总的行数：2533688  完美行数：951909  错误行数：1581779
    字数完美率：28.45% 字数错误率：71.54% 总的字数：28374428 完美字数：8074021 错误字数：20300407
    
    27、IKAnalyzer 智能切分：
    分词速度：319.28085 字符/毫秒
    行数完美率：37.55%  行数错误率：62.44%  总的行数：2533686  完美行数：951638  错误行数：1582048
    字数完美率：27.97% 字数错误率：72.02% 总的字数：28374416 完美字数：7938726 错误字数：20435690
    
    28、word分词 正向最小匹配算法：
    分词速度：2228.9465 字符/毫秒
    行数完美率：36.7%  行数错误率：63.29%  总的行数：2533709  完美行数：930069  错误行数：1603640
    字数完美率：26.72% 字数错误率：73.27% 总的字数：28374490 完美字数：7583741 错误字数：20790749
    
    29、Jieba INDEX：
    分词速度：861.55615 字符/毫秒
    行数完美率：36.02%  行数错误率：63.97%  总的行数：2533709  完美行数：912771  错误行数：1620938
    字数完美率：25.9% 字数错误率：74.09% 总的字数：28374490 完美字数：7351689 错误字数：21022801
    
    30、MMSeg4j MaxWordSeg：
    分词速度：1737.2491 字符/毫秒
    行数完美率：34.27%  行数错误率：65.72%  总的行数：2533688  完美行数：868440  错误行数：1665248
    字数完美率：25.2% 字数错误率：74.79% 总的字数：28374428 完美字数：7152898 错误字数：21221530
    
    31、IKAnalyzer 细粒度切分：
    分词速度：323.76926 字符/毫秒
    行数完美率：18.87%  行数错误率：81.12%  总的行数：2533686  完美行数：478176  错误行数：2055510
    字数完美率：10.93% 字数错误率：89.06% 总的字数：28374416 完美字数：3103178 错误字数：25271238

	评估耗时：41分钟,42秒,725毫秒

	重点说明：
			关于分词速度，这个不是绝对的，每次测试都会有些差距，而完美率是固定的，所以按行数完美率排名
			上面的评估报告中没有包括Stanford分词器和Paoding分词器
			当前代码已经移除了Paoding分词器，因为Paoding分词器已经7年没有维护了
			当前代码升级Stanford分词器到3.5.2，速度慢的无法等待评估完成，仅用于交互式效果对比
			下面是之前代码对 Paoding分词器2.0.4-beta 和 Stanford分词器 3.3.1 的评估数据

	Stanford Beijing University segmentation：
	分词速度：14.4612055 字符/毫秒
	行数完美率：58.29%  行数错误率：41.7%  总的行数：2533709  完美行数：1477034  错误行数：1056675
	字数完美率：51.36% 字数错误率：48.63% 总的字数：28374490 完美字数：14574120 错误字数：13800370

	Stanford Chinese Treebank segmentation：
	分词速度：13.723294 字符/毫秒
	行数完美率：55.45%  行数错误率：44.54%  总的行数：2533709  完美行数：1404968  错误行数：1128741
	字数完美率：47.27% 字数错误率：52.72% 总的字数：28374490 完美字数：13414926 错误字数：14959564

	Paoding MAX_WORD_LENGTH_MODE：
	分词速度：1343.1075 字符/毫秒
	行数完美率：14.19%  行数错误率：85.8%  总的行数：2533158  完美行数：359637  错误行数：2173521
	字数完美率：7.72% 字数错误率：92.27% 总的字数：28373102 完美字数：2191349 错误字数：26181753

	Paoding MOST_WORDS_MODE：
	分词速度：1338.9246 字符/毫秒
	行数完美率：11.6%  行数错误率：88.39%  总的行数：2533158  完美行数：294011  错误行数：2239147
	字数完美率：5.92% 字数错误率：94.07% 总的字数：28373102 完美字数：1680261 错误字数：26692841

### 效果对比：

####1、以 我爱楚离陌 为例子：
	
	word分词器 的分词结果：
		1 、【全切分算法】	我 爱 楚离陌 
    	2 、【双向最大最小匹配算法】	我 爱 楚离陌 
    	3 、【最大Ngram分值算法】	我 爱 楚离陌 
    	4 、【正向最大匹配算法】	我 爱 楚离陌 
    	5 、【双向最大匹配算法】	我 爱 楚离陌 
    	6 、【最少词数算法】	我 爱 楚离陌 
    	7 、【逆向最大匹配算法】	我 爱 楚离陌 
    	8 、【正向最小匹配算法】	我 爱 楚离陌 
    	9 、【双向最小匹配算法】	我 爱 楚离陌 
    	10 、【逆向最小匹配算法】	我 爱 楚离陌 
	Stanford分词器 的分词结果：
		1 、【Stanford Chinese Treebank segmentation】	我 爱 楚离陌 
		2 、【Stanford Beijing University segmentation】	我 爱 楚 离陌 
	Ansj分词器 的分词结果：
		1 、【BaseAnalysis】	我 爱 楚 离 陌 
		2 、【IndexAnalysis】	我 爱 楚 离 陌 
		3 、【ToAnalysis】	我 爱 楚 离 陌 
		4 、【NlpAnalysis】	我 爱 楚离 陌 
	HanLP分词器 的分词结果：
		1 、【NLP分词】 我 爱 楚 离 陌 
		2 、【标准分词】  我 爱 楚 离 陌 
		3 、【N-最短路径分词】  我 爱 楚 离 陌 
		4 、【索引分词】  我 爱 楚 离 陌 
		5 、【最短路径分词】    我 爱 楚 离 陌 
		6 、【极速词典分词】    我 爱 楚 离 陌 
	smartcn分词器 的分词结果：
		1 、【smartcn】	我 爱 楚 离 陌 
	FudanNLP分词器 的分词结果：
		1 、【FudanNLP】	我 爱楚离陌
	Jieba分词器 的分词结果：
		1 、【SEARCH】	我爱楚 离 陌 
		2 、【INDEX】	我爱楚 离 陌 
	Jcseg分词器 的分词结果：
		1 、【简易模式】	我 爱 楚 离 陌 
		2 、【复杂模式】	我 爱 楚 离 陌 
	MMSeg4j分词器 的分词结果：
		1 、【SimpleSeg】	我爱 楚 离 陌 
		2 、【ComplexSeg】	我爱 楚 离 陌 
		3 、【MaxWordSeg】	我爱 楚 离 陌 
	IKAnalyzer分词器 的分词结果：
		1 、【智能切分】	我 爱 楚 离 陌 
		2 、【细粒度切分】	我 爱 楚 离 陌 
		
####2、以 结合成分子 为例子：
    
    word分词器 的分词结果：
    	1 、【全切分算法】	结合 成 分子 
    	2 、【双向最大最小匹配算法】	结 合成 分子 
    	3 、【最大Ngram分值算法】	结合 成 分子 
    	4 、【正向最大匹配算法】	结合 成分 子 
    	5 、【双向最大匹配算法】	结 合成 分子 
    	6 、【最少词数算法】	结合 成 分子 
    	7 、【逆向最大匹配算法】	结 合成 分子 
    	8 、【正向最小匹配算法】	结合 成分 子 
    	9 、【双向最小匹配算法】	结 合成 分子 
    	10 、【逆向最小匹配算法】	结 合成 分子 
    Stanford分词器 的分词结果：
    	1 、【Stanford Chinese Treebank segmentation】	结合 成 分子 
    	2 、【Stanford Beijing University segmentation】	结合 成 分子 
    Ansj分词器 的分词结果：
    	1 、【BaseAnalysis】	结合 成 分子 
    	2 、【IndexAnalysis】	结合 成 分子 
    	3 、【ToAnalysis】	结合 成 分子 
    	4 、【NlpAnalysis】	结合 成 分子 
    HanLP分词器 的分词结果：
    	1 、【NLP分词】	结合 成 分子 
    	2 、【标准分词】	结合 成 分子 
    	3 、【N-最短路径分词】	结合 成 分子 
    	4 、【索引分词】	结合 成 分子 
    	5 、【最短路径分词】	结合 成 分子 
    	6 、【极速词典分词】	结合 成分 子 
    smartcn分词器 的分词结果：
    	1 、【smartcn】	结合 成 分子 
    FudanNLP分词器 的分词结果：
    	1 、【FudanNLP】	结合 成 分子
    Jieba分词器 的分词结果：
    	1 、【SEARCH】	结合 成 分子 
    	2 、【INDEX】	结合 成 分子 
    Jcseg分词器 的分词结果：
    	1 、【简易模式】	结合 成分 子 
    	2 、【复杂模式】	结合 成 分子 
    MMSeg4j分词器 的分词结果：
    	1 、【SimpleSeg】	结合 成分 子 
    	2 、【ComplexSeg】	结合 成分 子 
    	3 、【MaxWordSeg】	结合 成分 子 
    IKAnalyzer分词器 的分词结果：
    	1 、【智能切分】	结合 成 分子 
    	2 、【细粒度切分】	结合 合成 成分 分子
    	
###速度对比：
   
    1、HanLP分词器 极速词典分词：
    分词速度：5030.1978 字符/毫秒
    
    2、MMSeg4j MaxWordSeg：
    分词速度：2454.494 字符/毫秒
    
    3、MMSeg4j SimpleSeg：
    分词速度：2184.697 字符/毫秒
    
    4、word分词 逆向最小匹配算法：
    分词速度：1407.4127 字符/毫秒
    
    5、word分词 正向最小匹配算法：
    分词速度：1234.6848 字符/毫秒
    
    6、MMSeg4j ComplexSeg：
    分词速度：1184.436 字符/毫秒
    
    7、Jcseg 简易模式：
    分词速度：1023.73364 字符/毫秒
    
    8、Ansj BaseAnalysis 基本分词：
    分词速度：906.4427 字符/毫秒
    
    9、word分词 双向最小匹配算法：
    分词速度：833.2229 字符/毫秒
    
    10、Jieba SEARCH：
    分词速度：831.52246 字符/毫秒
    
    11、word分词 逆向最大匹配算法：
    分词速度：808.4246 字符/毫秒
    
    12、IKAnalyzer 细粒度切分：
    分词速度：735.4621 字符/毫秒
    
    13、HanLP分词器 索引分词：
    分词速度：664.67535 字符/毫秒
    
    14、word分词 正向最大匹配算法：
    分词速度：573.46375 字符/毫秒
    
    15、word分词 双向最大匹配算法：
    分词速度：539.6636 字符/毫秒
    
    16、Jieba INDEX：
    分词速度：507.40472 字符/毫秒
    
    17、word分词 双向最大最小匹配算法：
    分词速度：505.20273 字符/毫秒
    
    18、IKAnalyzer 智能切分：
    分词速度：483.90262 字符/毫秒
    
    19、HanLP分词器 标准分词：
    分词速度：461.43375 字符/毫秒
    
    20、Ansj IndexAnalysis 面向索引的分词：
    分词速度：446.76096 字符/毫秒
    
    21、word分词 最少词数算法：
    分词速度：444.56738 字符/毫秒
    
    22、Ansj ToAnalysis 精准分词：
    分词速度：440.2442 字符/毫秒
    
    23、word分词 最大Ngram分值算法：
    分词速度：419.61484 字符/毫秒
    
    24、smartcn：
    分词速度：419.39886 字符/毫秒
    
    25、Jcseg 复杂模式：
    分词速度：391.21075 字符/毫秒
    
    26、HanLP分词器 最短路径分词：
    分词速度：288.55948 字符/毫秒
    
    27、HanLP分词器 NLP分词：
    分词速度：251.66522 字符/毫秒
    
    28、Ansj NlpAnalysis NLP分词：
    分词速度：174.01068 字符/毫秒
    
    29、word分词 全切分算法：
    分词速度：146.16898 字符/毫秒
    
    30、FudanNLP：
    分词速度：111.7975 字符/毫秒
    
    31、HanLP分词器 N-最短路径分词：
    分词速度：67.67644 字符/毫秒

### 支持的分词器有：

   [1、word分词器](https://github.com/ysc/word)
    
   [2、ansj分词器](https://github.com/ansjsun/ansj_seg)
    
   [3、mmseg4j分词器](http://code.google.com/p/mmseg4j/)
   
   [4、ik-analyzer分词器](http://code.google.com/p/ik-analyzer/)
   
   [5、jcseg分词器](https://code.google.com/p/jcseg/)
   
   [6、fudannlp分词器](https://code.google.com/p/fudannlp/)
   
   [7、smartcn分词器](http://lucene.apache.org/core/5_1_0/analyzers-smartcn/org/apache/lucene/analysis/cn/smart/SmartChineseAnalyzer.html)
   
   [8、jieba分词器](https://github.com/huaban/jieba-analysis)
   
   [9、stanford分词器](http://nlp.stanford.edu/software/segmenter.shtml)
   
   [10、hanlp分词器](https://github.com/hankcs/HanLP)

[https://travis-ci.org/ysc/cws_evaluation](https://travis-ci.org/ysc/cws_evaluation)

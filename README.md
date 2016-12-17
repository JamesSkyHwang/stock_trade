# Overview
This code is based on KRX (Korea Exchange) trade system. For the trading convenience, users easily can define their rule sets so that the computer buy and sell according to them. This code suits scalping strategy well. eBest investment company uploaded their own API on their web site. (http://www.ebestsec.co.kr/)

# Example eBest Process Overview
![overview](https://github.com/yoonsungkim87/stock_trade/blob/master/stock_ebest.png)

# Example Archiving Result
Archiving process print out codes' name (up to 50) first, and then price, quantity, residual selling quantity, residual buying quantity, volume-power. (5 attributes) At the end of the line, timestamps will be printed for future analysis. In total, 251 attributes recorded in a line at most (= 5attributes * 50codes [maximum case] + 1time stamp) In the example below, '유니크' has 3550 prices, 4469 cumulative volumes, 0 of residual selling quantity, residual buying quantity, and volume power at 2016-12-16 08:55:16.433000.
```
유니크|동국실업|광림|CJ씨푸드|KODEX 200선물인버스2|삼화페인트|옵트론텍|알루코|해마로푸드서비스|대성파인텍|광진윈텍|손오공|TIGER 200선물인버스2|흥국화재|골든센츄리|한탑|동화약품|KODEX 코스닥150 레버|서연탑메탈|네이처셀|유유제약|유유제약1우|삼일제약|홈센타홀딩스|솔고바이오|파인디앤씨|좋은사람들|쌍방울|진양제약|대원강업|썬코어|티플랙스|한창|팬오션|신라섬유|케이탑리츠|DSR제강|세우글로벌|씨씨에스|피제이전자|원풍물산|아비스타|카프로|썬텍|텔콘|지엔코|파루|SK증권|대신정보통신|한국팩키지|
3550|4469|0|0|0.0|2725|1400|0|0|0.0|7600|4914|0|0|0.0|3635|1000|0|0|0.0|9520|55|0|0|0.0|9990|0|0|0|0.0|5560|5834|0|0|0.0|5160|8527|0|0|0.0|1935|3706|0|0|0.0|2735|5808|0|0|0.0|5450|3364|0|0|0.0|6590|512|0|0|0.0|9555|600|0|0|0.0|3615|0|0|0|0.0|6780|200|0|0|0.0|2245|0|0|0|0.0|7940|0|0|0|0.0|8195|3633|0|0|0.0|9510|11132|0|0|0.0|4660|500|0|0|0.0|9350|0|0|0|0.0|5760|0|0|0|0.0|8090|0|0|0|0.0|4810|37454|0|0|0.0|1040|3118|0|0|0.0|8390|11|0|0|0.0|2460|25545|0|0|0.0|2030|780|0|0|0.0|4830|0|0|0|0.0|4135|0|0|0|0.0|4050|38766|0|0|0.0|2425|3803|0|0|0.0|5950|3388|0|0|0.0|3800|8715|0|0|0.0|2480|0|0|0|0.0|1900|3000|0|0|0.0|8750|2261|0|0|0.0|2025|32282|0|0|0.0|2300|5178|0|0|0.0|7650|0|0|0|0.0|3405|99|0|0|0.0|1055|1102|0|0|0.0|5980|1287|0|0|0.0|2830|8370|0|0|0.0|4230|10|0|0|0.0|8100|1266|0|0|0.0|4290|0|0|0|0.0|1055|1133|0|0|0.0|2945|16893|0|0|0.0|3495|14972|0|0|0.0|2016-12-16 08:55:16.433000
3550|4469|0|0|0.0|2725|1400|0|0|0.0|7600|4914|0|0|0.0|3635|1000|0|0|0.0|9520|55|0|0|0.0|9990|0|0|0|0.0|5560|5834|0|0|0.0|5160|8527|0|0|0.0|1935|3706|0|0|0.0|2735|5808|0|0|0.0|5450|3364|0|0|0.0|6590|512|0|0|0.0|9555|600|0|0|0.0|3615|0|0|0|0.0|6780|200|0|0|0.0|2245|0|0|0|0.0|7940|0|0|0|0.0|8195|3633|0|0|0.0|9510|11132|0|0|0.0|4660|500|0|0|0.0|9350|0|0|0|0.0|5760|0|0|0|0.0|8090|0|0|0|0.0|4810|37454|0|0|0.0|1040|3118|0|0|0.0|8390|11|0|0|0.0|2460|25545|0|0|0.0|2030|780|0|0|0.0|4830|0|0|0|0.0|4135|0|0|0|0.0|4050|38766|0|0|0.0|2425|3803|0|0|0.0|5950|3388|0|0|0.0|3800|8715|0|0|0.0|2480|0|0|0|0.0|1900|3000|0|0|0.0|8750|2261|0|0|0.0|2025|32282|0|0|0.0|2300|5178|0|0|0.0|7650|0|0|0|0.0|3405|99|0|0|0.0|1055|1102|0|0|0.0|5980|1287|0|0|0.0|2830|8370|0|0|0.0|4230|10|0|0|0.0|8100|1266|0|0|0.0|4290|0|0|0|0.0|1055|1133|0|0|0.0|2945|16893|0|0|0.0|3495|14972|0|0|0.0|2016-12-16 08:55:17.868000
```

# Example Simulation Trade Result
When you apply your strategy to real trade market, it is kind of burden for users to spend money for testing. To prevent this, users can simulate result, according to those rule sets which user defines. In the example below, '한국팩키지' is bought with a price of 3535 (first line), and sold at 3560 (fourth line).
```
2016-12-16 10:01:48.870000|037230|한국팩키지|3535|buy
2016-12-16 10:12:07.286000|019770|서연탑메탈|9430|buy
2016-12-16 10:12:12.060000|019770|서연탑메탈|9440|sell
2016-12-16 10:12:15.601000|037230|한국팩키지|3560|sell
2016-12-16 10:14:45.970000|051170|썬코어|4000|buy
2016-12-16 10:15:19.338000|900280|골든센츄리|7030|buy
2016-12-16 10:15:29.572000|900280|골든센츄리|7030|sell
2016-12-16 10:18:53.667000|043100|솔고바이오|1090|buy
2016-12-16 10:25:42.731000|051170|썬코어|4030|sell
2016-12-16 10:31:15.558000|043100|솔고바이오|1125|sell
2016-12-16 10:32:12.077000|011150|CJ씨푸드|3670|buy
2016-12-16 10:34:00.684000|066910|손오공|7380|buy
2016-12-16 10:37:56.619000|043200|파루|4420|buy
2016-12-16 10:47:14.257000|011150|CJ씨푸드|3650|sell
2016-12-16 10:47:58.483000|066910|손오공|7390|sell
2016-12-16 10:53:12.824000|043200|파루|4395|sell
2016-12-16 10:59:38.753000|020180|대신정보통신|2940|buy
2016-12-16 10:59:41.561000|020180|대신정보통신|2940|sell
2016-12-16 11:00:11.934000|122800|썬텍|2850|buy
2016-12-16 11:01:00.513000|013000|세우글로벌|2045|buy
2016-12-16 11:01:02.151000|013000|세우글로벌|2045|sell
2016-12-16 11:11:56.042000|122800|썬텍|2835|sell
2016-12-16 11:43:46.702000|007370|진양제약|5220|buy
2016-12-16 11:52:07.821000|007370|진양제약|5150|sell
2016-12-16 12:14:45.663000|000225|유유제약1우|5920|buy
2016-12-16 12:28:32.590000|000225|유유제약1우|5900|sell
2016-12-16 12:47:09.692000|060560|홈센타홀딩스|4815|buy
2016-12-16 12:47:13.966000|060560|홈센타홀딩스|4815|sell
2016-12-16 15:12:00.748000|001780|알루코|5190|buy
2016-12-16 15:12:03.618000|001780|알루코|5180|sell
```
# 数据附录

采集时间：2026-10-29 UTC。序列窗口：2021-10-24 至 2026-10-25，共 262 周。均值、同比和月份轮廓都去掉了最后一周（`isPartial=true`，日期 2026-10-25）。

## 1. 采集

- 库：pytrends 4.9.2，`TrendReq(hl=按国家, tz=0, timeout=(12, 40), retries=0, backoff_factor=0)`。
- `retries=0` 的原因：pytrends 在重试时向 urllib3 传入已删除的参数 `method_whitelist`，打开重试会直接抛 `TypeError`。429 由采集脚本自己退避。
- 全球：`geo=""`。pytrends 的 `build_payload` 写的是 `self.geo = geo or self.geo`，空字符串会沿用上一次的国家。每次全球请求前先把 `py.geo` 设成 `""`。
- 兴趣随时间与国家地图：`today 5-y`，类别 0，网页搜索。国家地图 `resolution=COUNTRY`，`inc_low_vol=False`，`inc_geo_code=True`。
- 相关查询：`today 12-m`，全球，`hl=en-US`。
- 本地比较的界面语言：德国 `de`，巴西 `pt-BR`，印度 `en-IN`，英国 `en-GB`，美国 `en-US`，法国 `fr`，西班牙 `es`。
- 指数是该次请求内部的 0–100，不是搜索次数。一次最多 5 个词。100 等于这 5 条曲线里最高的那一周。换一组词，尺子就变。跨组只引用比值。
- 国家指数是「该词占该国搜索的比例」在本次比较中的相对值。小国可以高于大国。低搜索量的词会把稀疏国家舍入到 66 或 100，正文以相关查询和目标国是否为 0 来判断。

同组稳定性核对（重叠词的周均在两批里相同，因为峰值词没变，尺子没变）：

| 词 | `w_giants` | `w_finalists2` |
| --- | ---: | ---: |
| ielts | 72.52 | 72.52 |
| resume template | 8.41 | 8.41 |
| invoice template | 4.21 | 4.21 |

| 词 | `w_wedge` | `w_finalists` |
| --- | ---: | ---: |
| cancel subscription | 36.23 | 36.23 |
| ielts writing | 9.15 | 9.15 |
| invoice template | 7.25 | 7.25 |

比值核对：

| 比值 | 批次 A | 批次 B |
| --- | ---: | ---: |
| cancel subscription / invoice template | 21.08 / 4.21 = 5.01（`w_finalists2`） | 36.23 / 7.25 = 5.00（`w_finalists`） |
| personal statement / invoice template | 15.95 / 7.25 = 2.20（`w_finalists`） | 26.05 / 11.77 = 2.21（`w_acad`） |

## 2. 终选同尺度

`w_finalists`，全球，近 5 年。周均：

| 词 | 周均 | / invoice template |
| --- | ---: | ---: |
| cancel subscription | 36.23 | 5.00 |
| personal statement | 15.95 | 2.20 |
| ielts writing | 9.15 | 1.26 |
| invoice template | 7.25 | 1 |
| motivation letter | 3.29 | 0.45 |

国家份额（本次比较内）：

| 国家 | cancel subscription | personal statement | ielts writing | invoice template | motivation letter |
| --- | ---: | ---: | ---: | ---: | ---: |
| US | 66 | 24 | 0 | 10 | 0 |
| GB | 52 | 37 | 2 | 9 | 0 |
| IN | 27 | 17 | 44 | 8 | 4 |
| DE | 57 | 14 | 5 | 5 | 19 |
| BR | 52 | 33 | 6 | 6 | 3 |

`cancel subscription` 指数 ≥20 的国家 47 个。前部：IL 73，DK 72，NO 72，SE 72，RO 71，AU 67，CZ 67，US 66，IE 65，FI 64，MX 62，GR 61。

`ielts writing` 指数 ≥20：VN 85，BD 68，IN 44，PK 43，TH 42，TR 39，TW 29，SA 27，HK 25，JP 25，AE 22，ID 21。共 14 个。

`personal statement` 指数 ≥20 的前部：HK 45，GB 37，BR 33，NG 33，KR 33，PH 30，KE 29，TW 28，SG 26，AR 25，US 24，PK 23。共 19 个。

`motivation letter` 指数 ≥20：ID 33，MA 32，BE 29，NL 26，CH 26，AT 25，FR 25，HU 24，ZA 21。共 9 个。

`w_finalists2`，全球，近 5 年。周均：

| 词 | 周均 | / invoice template |
| --- | ---: | ---: |
| ielts | 72.52 | 17.23 |
| cover letter | 30.68 | 7.29 |
| cancel subscription | 21.08 | 5.01 |
| resume template | 8.41 | 2.00 |
| invoice template | 4.21 | 1 |

国家份额：

| 国家 | ielts | cover letter | cancel subscription | resume template | invoice template |
| --- | ---: | ---: | ---: | ---: | ---: |
| US | 6 | 40 | 38 | 11 | 5 |
| GB | 22 | 32 | 38 | 1 | 7 |
| IN | 78 | 10 | 3 | 8 | 1 |
| DE | 41 | 30 | 23 | 4 | 2 |
| BR | 50 | 27 | 18 | 3 | 2 |

这一组里美国和英国的雅思份额低于 `w_giants`，因为求职信和退订占掉了份额。见第 4 节。

## 3. 各批周均与锚点比值

下面「/发票」只在该批含有 `invoice template` 时计算。

### w_giants

ielts 72.52（17.23×），toefl 16.48（3.91×），acca 13.72（3.26×），resume template 8.41（2.00×），invoice template 4.21。

| 国家 | ielts | toefl | acca | resume template | invoice template |
| --- | ---: | ---: | ---: | ---: | ---: |
| US | 20 | 18 | 5 | 38 | 19 |
| GB | 37 | 3 | 47 | 2 | 11 |
| IN | 73 | 6 | 13 | 7 | 1 |
| DE | 47 | 38 | 9 | 4 | 2 |
| BR | 36 | 55 | 5 | 3 | 1 |
| MX | 20 | 76 | 1 | 2 | 1 |
| ID | 33 | 65 | 0 | 1 | 1 |
| FR | 35 | 42 | 19 | 3 | 1 |
| PK | 67 | 2 | 28 | 2 | 1 |
| NG | 81 | 5 | 9 | 3 | 2 |
| PH | 54 | 5 | 2 | 37 | 2 |
| CA | 79 | 4 | 3 | 9 | 5 |
| AU | 58 | 3 | 5 | 20 | 14 |
| VN | 95 | 3 | 2 | 0 | 0 |
| JP | 45 | 46 | 8 | 1 | 0 |

### w_job

cover letter 49.14，resume template 13.44，cv template 11.68，resume builder 8.80，cover letter template 3.38。

| 国家 | cover letter | resume template | cv template | resume builder | cover letter template |
| --- | ---: | ---: | ---: | ---: | ---: |
| US | 61 | 16 | 2 | 16 | 5 |
| GB | 62 | 3 | 30 | 1 | 4 |
| IN | 37 | 27 | 8 | 27 | 1 |
| DE | 61 | 9 | 23 | 4 | 3 |
| BR | 75 | 11 | 8 | 4 | 2 |
| PH | 56 | 32 | 7 | 3 | 2 |
| ID | 41 | 4 | 53 | 1 | 1 |
| PK | 41 | 10 | 41 | 6 | 2 |
| NG | 67 | 6 | 20 | 5 | 2 |
| FR | 56 | 7 | 32 | 3 | 2 |
| ES | 69 | 6 | 19 | 3 | 3 |

### w_money

invoice template 55.16，invoice generator 21.22（0.38×），payment reminder 5.61（0.10×），quotation template 5.57（0.10×），timesheet template 3.53（0.064×）。

| 国家 | invoice template | invoice generator | quotation template | timesheet template | payment reminder |
| --- | ---: | ---: | ---: | ---: | ---: |
| US | 72 | 19 | 0 | 5 | 4 |
| GB | 71 | 21 | 2 | 3 | 3 |
| IN | 34 | 44 | 7 | 1 | 14 |
| DE | 57 | 24 | 4 | 4 | 11 |
| BR | 54 | 31 | 3 | 4 | 8 |
| CA | 65 | 27 | 1 | 4 | 3 |
| AU | 72 | 21 | 1 | 4 | 2 |
| FR | 58 | 25 | 5 | 5 | 7 |
| ES | 56 | 30 | 4 | 3 | 7 |
| MX | 57 | 28 | 6 | 2 | 7 |
| ID | 57 | 32 | 8 | 1 | 2 |
| PH | 39 | 19 | 18 | 3 | 21 |
| NG | 45 | 39 | 6 | 0 | 10 |
| PK | 35 | 55 | 7 | 0 | 3 |

### w_wedge

cancel subscription 36.23，ielts writing 9.15，statement of purpose 7.64（1.05×发票），invoice template 7.25，upwork proposal 0.23（0.006×退订）。

| 国家 | cancel subscription | ielts writing | statement of purpose | invoice template | upwork proposal |
| --- | ---: | ---: | ---: | ---: | ---: |
| US | 71 | 0 | 18 | 11 | 0 |
| GB | 80 | 3 | 2 | 15 | 0 |
| IN | 26 | 43 | 23 | 8 | 0 |
| DE | 79 | 8 | 5 | 8 | 0 |
| BR | 76 | 9 | 6 | 9 | 0 |
| NG | 34 | 17 | 35 | 10 | 4 |
| PH | 53 | 7 | 33 | 5 | 2 |
| PK | 15 | 50 | 15 | 11 | 9 |
| ID | 31 | 37 | 11 | 20 | 1 |
| FR | 73 | 11 | 5 | 11 | 0 |
| ES | 77 | 10 | 4 | 9 | 0 |
| MX | 76 | 8 | 8 | 8 | 0 |

### w_travel

invoice template 27.33，warranty claim 25.15（0.92×），cancel netflix 13.76（0.50×），flight delay compensation 7.22（0.26×），schengen calculator 1.30（0.05×）。

| 国家 | warranty claim | flight delay compensation | cancel netflix | schengen calculator | invoice template |
| --- | ---: | ---: | ---: | ---: | ---: |
| US | 35 | 6 | 21 | 0 | 38 |
| GB | 15 | 26 | 20 | 3 | 36 |
| IN | 78 | 2 | 8 | 0 | 12 |
| DE | 13 | 26 | 21 | 13 | 27 |
| BR | 10 | 7 | 52 | 1 | 30 |
| ES | 6 | 35 | 20 | 18 | 21 |
| FR | 9 | 26 | 26 | 10 | 29 |
| CA | 26 | 15 | 19 | 0 | 40 |
| MX | 13 | 20 | 34 | 2 | 31 |
| AU | 27 | 2 | 16 | 0 | 55 |
| PK | 36 | 2 | 11 | 1 | 50 |

### w_life

invoice template 55.16，expense tracker 11.49（0.21×），meal plan template 2.18（0.04×），media kit template 0.70，youtube script template 0.44。

### w_acad

personal statement 26.05（2.21×），scholarship application 12.46（1.06×），invoice template 11.77，cfa exam 3.70（0.31×），freelance contract 1.33。

| 国家 | personal statement | scholarship application | cfa exam | invoice template |
| --- | ---: | ---: | ---: | ---: |
| US | 56 | 16 | 4 | 23 |
| GB | 74 | 3 | 3 | 19 |
| IN | 22 | 51 | 17 | 10 |
| DE | 44 | 20 | 12 | 18 |
| BR | 65 | 14 | 7 | 12 |
| NG | 42 | 43 | 3 | 12 |
| PH | 46 | 45 | 1 | 7 |
| PK | 36 | 45 | 3 | 16 |
| KE | 23 | 58 | 1 | 18 |

`w_acad` 的尺子比 `w_finalists` 松，因为这组里没有退订。国家指数不能和终选表混比。个人陈述 / 发票的比值两边都是 2.2。

### w_docs

motivation letter 50.19，quotation template 11.11，dmca takedown 4.74，statement of work template 2.15，podcast show notes 1.82。

这一组没有发票模板。动机信 / 报价模板 = 4.52。报价模板 / 发票模板在 `w_money` 是 0.101。链式估计 0.46，和终选组直接测到的 0.45 一致。链式值只作核对，正文用终选组的 0.45。

动机信在本组的高份额国家包括 GH、RW、BE、HU、ID、NL、TR、FR（都在 93 以上）。这是份额，而且动机信在这组里压过了其他四个小词。终选组把它放在退订旁边之后，美国和英国掉到 0，法国、德国、荷比仍然可见。以终选组为准。

### w_cancel

cancel subscription 36.23，cancel amazon prime 4.4，cancel spotify 3.4，cancel disney plus 1.4，subscription tracker 1.0。

`subscription tracker` 的相关查询被 GPS 和手环污染，见第 7 节。单独国家图也只反映这个被污染的词：GB 100，US 64，CA 52，AU 47，DE 11，IN 5，BR 0。不作为退订需求的证据。

### w_exams

invoice template 55.16，ielts writing task 2 20.7（0.38×），cfa exam 17.4（0.32×），pmp exam 13.5（0.24×），acca exam 13.5（0.24×）。

`ielts writing task 2` 指数 ≥20 的国家：BD、KH、CO、GH、IN、ID、IR、IT、PK、PH、RU、LK、TW、TH、TR、UA、VN。美国、英国、德国、巴西不在 ≥20 里。

`pmp exam` 指数 ≥20：EG、DE、IT、JP、QA、SA。

`acca exam` 指数 ≥20：KH、IE、MY、PK、PL、SG、TT、UG、AE、GB、ZM、ZW。

`cfa exam` 指数 ≥20：AR、BE、BR、FR、DE、HK、IN、JP、MX、NL、SG、KR、ES、CH。

### w_free

invoice template 55.16，fiverr gig 12.5（0.23×），freelance invoice 1.9，invoice reminder 1.3，late payment reminder 0.1。

`fiverr gig` 指数 ≥20：AR、BD、BR、CO、EG、FR、DE、GR、IN、IT、NG、PL、LK、TR、UA。未做相关查询，不区分买家和卖家。

### w_time

invoice template 55.16，stundenzettel 4.22，timesheet template 3.53，time sheet template 2.66，weekly timesheet 0.98。

德国在这组里：invoice template 8，stundenzettel 91，英语工时词接近 0。`stundenzettel` 是德国词。英语工时词在美国、英国大约是发票模板的十几分之一（US：发票 88，timesheet template 6，time sheet template 5）。

### w_creator

invoice template 55.16，rate card template 1.57，podcast show notes 1.06，youtube script template 0.44，brand deal contract 0.23。目标国里这些创作者词大多是 0–3。

## 4. 季节性

月份是 5 年里该月各周的平均。同比 = 最后 52 个完整周的均值 / 再往前 52 周。相对 2023 = 2025 与 2026 年各周均值 / 2023 年各周均值。变异系数是总体标准差 / 均值。

| 词 | 批次 | 峰值月 | 低值月 | 高低比 | 变异系数 | 同比 | 相对 2023 |
| --- | --- | --- | --- | ---: | ---: | ---: | ---: |
| ielts | w_giants | 08 | 04 | 1.25 | 0.16 | 1.09 | 0.82 |
| ielts writing | w_wedge | 07 | 12 | 1.23 | 0.16 | 1.08 | 0.82 |
| ielts writing task 2 | w_exams | 07 | 12 | 1.24 | 0.25 | 1.13 | 0.67 |
| toefl | w_giants | 08 | 12 | 1.29 | 0.15 | 1.12 | 1.07 |
| cancel subscription | w_wedge | 08 | 10 | 1.30 | 0.45 | 1.68 | 2.03 |
| cover letter | w_job | 02 | 12 | 1.68 | 0.21 | 1.30 | 0.98 |
| personal statement | w_acad | 09 | 12 | 1.73 | 0.48 | 2.04 | 1.67 |
| motivation letter | w_docs | 01 | 07 | 1.66 | 0.31 | 1.13 | 0.66 |
| resume template | w_job | 05 | 12 | 1.54 | 0.23 | 1.12 | 1.21 |
| cv template | w_job | 07 | 12 | 1.52 | 0.17 | 0.91 | 0.93 |
| invoice template | w_money | 06 | 12 | 1.37 | 0.20 | 1.23 | 1.26 |
| invoice generator | w_money | 08 | 12 | 1.27 | 0.26 | 1.10 | 1.48 |
| warranty claim | w_travel | 08 | 02 | 1.39 | 0.26 | 1.29 | 1.26 |
| flight delay compensation | w_travel | 08 | 11 | 2.37 | 0.48 | 1.21 | 1.26 |
| scholarship application | w_acad | 08 | 04 | 1.81 | 0.53 | 1.74 | 1.92 |
| statement of purpose | w_wedge | 02 | 07 | 1.89 | 0.23 | 1.03 | 0.92 |
| expense tracker | w_life | 09 | 10 | 1.37 | 0.53 | 1.53 | 2.14 |
| cancel netflix | w_travel | 02 | 10 | 2.17 | 0.82 | 2.45 | 2.36 |

`cancel subscription` 的变异系数高，是因为水平在涨，不是单月尖峰。美国国内月均（`gA_US`，该国比较内部的尺子）：1 月 51.0，2 月 52.1，3 月 48.5，4 月 45.8，5 月 48.8，6 月 52.7，7 月 52.5，8 月 51.2，9 月 50.5，10 月 46.0，11 月 46.2，12 月 47.8。

英国 `gA_GB` 退订月均在 43–52。印度 `gA_IN`：8 月 31.6 最高，10 月 19.9 最低。德国 `gA_DE`：2 月 21.4 最高，10 月 9.9 最低，全年都有读数。巴西 `gA_BR`：8 月 14.0，10 月 2.1，1 月 4.9，年中更高，但不是只有一个月。

这些 `gA_*` 数字是各国内部比较的尺子，不能把德国的 14 和美国的 49 相除。跨国用第 2 节的份额。

印度 `gA_IN` 内部周均：resume template 53.07，ielts writing 35.39，cancel subscription 23.73，invoice template 7.07，timesheet template 0.05。写作在印度是日常水平：7 月 40.9，3 月 31.2。

美国 `gA_US` 内部周均：cancel subscription 49.41，resume template 15.05，invoice template 7.16，timesheet template 0.56，ielts writing 0.30。

## 5. 本地语言

周均是该国这一组内部的尺子。

| 组 | 周均 |
| --- | --- |
| 德国 `l_de` | abo kündigen 71.78；lebenslauf vorlage 59.98；stundenzettel 12.81；rechnungsvorlage 3.76；flugentschädigung 0.85 |
| 德国 `l_de2` | motivationsschreiben 50.70；rechnungsvorlage 8.11；mahnschreiben 1.96；ielts writing 1.39；schengen rechner 0.07 |
| 巴西 `l_br` | nota fiscal 59.90；cancelar assinatura 3.53；carta de apresentação 1.29；modelo de currículo 1.20；modelo de fatura 0.0 |
| 印度 `l_in1` | resume format 65.10；resume template 27.72；cv format 19.75；ielts writing 18.48；invoice format 10.62 |
| 印度 `l_in2` | cover letter 51.93；gst invoice 37.61；cancel subscription 18.54；statement of purpose 15.92；upwork proposal 0.50 |
| 英国 `l_gb` | personal statement 19.32；self assessment tax 16.97；cv template 10.69；invoice template 4.90；flight delay compensation 3.39 |
| 美国 `l_us` | cancel subscription 49.41；resume template 15.05；invoice template 7.16；cover letter template 4.23；estimated quarterly taxes 0.50 |
| 西班牙 `l_es` | ielts 47.48；cancelar suscripción 41.60；carta de presentación 20.52；modelo de factura 11.88；modelo de curriculum 4.69 |
| 法国 `l_fr` | lettre de motivation 26.90；annuler abonnement 1.89；facture impayée 0.64；modèle de cv 0.48；modèle de facture 0.0 |
| 法国 `l_fr2` | lettre de motivation 26.90；résiliation 16.42；annuler abonnement 1.89；résilier abonnement 1.62；se désabonner 1.53 |

`résiliation` 不带 abonnement，包含租约、保险和其他合同解除，不用它代表订阅退订。法国退订的几种直接说法都远小于动机信。全球英语比较里法国对 `cancel subscription` 的份额仍然高（`w_wedge` 法国 73）。两件事同时成立。

`modelo de currículo` 和 `modèle de facture` 可能不是当地最常用的拼写。低分只否定这一个短语。巴西的英语 `cover letter` 份额和 `cv template` 另见第 3 节。

## 6. 国家锁定对照

单词单独查询，全球，近 5 年。100 是该词份额最高的国家。

| 词 | 周均（自身尺子） | 峰值月（月均） | 低值月 | 同比 | 目标国与备注 |
| --- | ---: | --- | --- | ---: | --- |
| estimated quarterly taxes | 18.46 | 04（38） | 11（8） | 1.61 | 只有美国 ≥20。英印德巴加澳法 = 0。相关查询：pay / how to pay / online / due dates |
| form 5472 | 11.38 | 04（19） | 12（5） | 3.26 | 美国 100。英印德巴 = 0。稀疏国家被舍入得很高（SG、SH 100，CA、CN、IL、MA、PK 66）。相关查询全是 irs form 5472、1120、instructions、pdf |
| irmaa | 26.42 | 11（35） | 07（21） | 2.05 | 美国 100。KR 6，BR 4，CA 2。英印德 = 0 |
| aca premium tax credit | 11.42 | 11（18） | 02（7） | 5.46 | 只有美国 ≥20 |
| property tax protest | 10.58 | 05（34） | 12（3） | 1.71 | 美国 100。KR 28、SH 42 视为低量噪声。目标国其余为 0 |
| student loan save plan | 11.1 | 08（21） | 11（6） | 1.27 | 只有美国 ≥20 |
| self assessment tax | 16.78 | 01（46） | 08（11） | 1.32 | 英国 100。IE 9，IN 4，AU 1。美国、德国、巴西 = 0 |
| steuererklärung | 37.44 | 07（50） | 11（24） | 1.02 | 德国 100，瑞士 61，卢森堡 16，奥地利 14。美英印巴 = 0。相关查询：2025/2026、Frist、ELSTER、Finanzamt、Rentner |
| imposto de renda | 16.46 | 05（44） | 12（6） | 1.03 | 巴西 100，葡萄牙 2。其余目标国 0。相关查询全是 2026 申报、退税查询、截止日期，上升值到两万以上 |
| gst invoice | 52.28 | 05（58） | 01（46） | 1.20 | 印度 100，新西兰 50，新加坡 44，澳大利亚 39，加拿大 6。美英德巴 = 0。相关查询：tax invoice、login、format、requirements、rules |

`nota fiscal` 没有做全球单词地图。巴西组里它的周均是 59.90，对 `cancelar assinatura` 3.53。

州 franchise tax 没有单独拉序列。

## 7. 相关查询

时间范围 `today 12-m`，全球。括号里是 Google 给出的相对值；上升列里的大数经常是 Breakout 级无关热搜。标了「污染」的不进入产品判断。

### 退订

`cancel subscription`

- 头部：how to cancel subscription (100)，adobe (17)，adobe subscription cancel (17)，how to cancel subscription on iphone (15)，how to cancel adobe subscription (15)，chatgpt cancel subscription (12)，amazon cancel subscription (10)，how to cancel chatgpt subscription (6)
- 上升：lidl near me (9750，污染)，how to cancel fox one subscription (600)，how to cancel adobe subscription (550)，how to cancel subscription on iphone (350)，how to cancel reelshort subscription (250)，adobe (200)，how to cancel hbo subscription (110)

`cancel netflix`

- 头部：how cancel netflix (100)，how to cancel netflix (96)，netflix subscription (26)，how to cancel netflix subscription (12)
- 上升：python programming tutorial (2100，污染)，how to cancel adobe subscription (200)

`subscription tracker`（词本身污染，不采用）

- 头部：gps tracker (100)，subscription tracker app (87)，fitness tracker (61)，free subscription tracker (57)，gps tracker no subscription (37)，car tracker (33)，sleep tracker (31)，dog tracker (31)，whoop (30)

### 考试

`ielts writing`

- 头部：ielts writing task (100)，task 1 (57)，task 2 (51)，pdf (22)，sample (14)，band descriptors (11)，task 2 2026 (10)，practice (8)
- 上升：đề thi ielts writing 2026 (35100)，ielts writing task 2 2026 (3650)，band descriptors (550 / 400)，sample answer pdf (90)，criteria (90)，engnovate (70)

`ielts`

- 头部：ielts test (100)，reading (52)，speaking (47)，writing (46)，listening (40)，online (32)，exam (30)，score (29)，cambridge (26)
- 上升：the ielts dictionary (800)，jumpinto ielts (600)，egnovate ielts (350)，ielts mate (300)，keen ielts (300)，cathoven (250)

`acca`

- 头部：acca exam (100)，what is acca (64)，my acca (60)，login (57)，course (57)，fees (41)，salary (38)，per (34)，jobs (30)
- 上升：acca september 2026 exam dates (2500)，past exams，study hub

`acca exam`

- 头部：fees (100)，dates (91)，what is (62)，registration (37)，results (35)
- 上升：december / september / june 2026 exam dates

### 求职与文书

`cover letter`

- 头部：what is cover letter (100)，what is a cover letter (83)，write a cover letter (79)，example (77)，how to write (72 / 70)，free (51)，examples (51)，resume (50)，resume cover letter (49)，for job (47)
- 上升：what is a cover letter example (2400)，what is a notarized letter (1600，污染)，cover letter example australia (350)，sample cover letter australia (190)，template australia (180)，how to write (170)

`cover letter template`

- 头部：free、pdf、word、resume cover letter template
- 上升：codashop (17750，污染)，pdf、rental cover letter template (450)、australia、reddit

`resume template`

- 头部：free、download、word、pdf
- 上升：codashop ml (12000，污染)，codashop (6550，污染)，ken coleman resume template (1050)，simple resume template free download (300)，australia (250)

`resume builder`

- 头部：free resume builder (100)，free resume (95)，resume ai builder (47)，best (32)，online (22)，ai resume builder free (18)，ats (12)
- 上升：best resume builder 2018 (950，旧查询)，teal ai resume builder (300)，teal (200)，rezi ai resume builder (200)

`cv template`

- 头部：free、download、word、pdf、resume
- 上升：australia cv template (400)，what is a cv vs resume (250)，jobstreet cv template (200)，english cv template (140)

`personal statement`

- 头部：what is a personal statement (100)，example (81)，how to write (67 / 64)，examples (25)，university (23)，for university (11)，ucas personal statement (11)，ucas (10)
- 上升：how to write (300 / 250)，example (140)，what is (60)

`motivation letter`

- 头部：university (100)，what is (81)，sample (72)，example (70)，what is a (46)，for university (45)，scholarship (39)，how to write (39)，for job (36)，template (35)，for scholarship (27)
- 上升：motivation letter ssu itb (38200，单一学校)，what is (80)，structure (70)，in english (50)

`statement of purpose`

- 头部：what is (100 / 85)，example (24)，meaning (12)，examples (11)，how to write (9)，purpose of income statement (9，会计污染)
- 上升：大段无关的选择题文本（身体自主、同意、情商），数值 350–750，整段作废。可用的尾巴：statement of purpose adalah (90)，template (80)，phd statement of purpose (60)

`scholarship application`

- 头部：form (100)，online (90)，general (25)，letter (21)，dost (18)，ssp (17)，common (16)
- 上升：mara scholarship application 2026 (8200)，dost scholarship application 2027 to 2028 (5150)，connect to work scholarship application status (3550)。国家级门户，不是全球表单。

### 账单

`invoice template`

- 头部：free invoice template (100)，free invoice (96)，template for invoice (77)，download (48)，pdf (47)，word (44)，excel (35)
- 上升：word doc (1050)，simple word (700)，simple free (550)，free pdf (500)，free online (300)，free invoice template australia (300)

`invoice generator`

- 头部：free invoice (100)，free invoice generator (97)，online (42)，best (25)，ai invoice generator (18)，pdf (15)
- 上升：ai note taker (5600，污染)，invoice generator australia (250)，best free (140)，ai invoice generator (110)

`quotation template`

- 头部：download、free download、pdf、word、excel、price quotation、business quotation。全是免费文件。

`payment reminder`

- 头部：reminder for payment (100)，email (40)，invoice payment reminder (21)，app (21)，message (20)，late (16)，template (15)，letter (14)，overdue (13)
- 上升：facebook user privacy settlement payment reminder (107900，污染)，final payment reminder (22050，污染)。其后才是 polite payment reminder email (140)、late (90)、invoice payment reminder (90)

`timesheet template`

- 头部：free (100)，excel (86)，weekly (37)，simple (20)，monthly (20)，employee (18)

`upwork proposal`（量小，列表短）

- 头部：template (100)，how to write (85)，sample (81)，generator (57)，cover letter for upwork proposal (40)
- 上升：空

### 其他被看过的词

`warranty claim`

- 头部：on warranty claim (100)，boat (44)，amazon (31)，apple (21)，samsung (21)，nike (8)，noise (8)，dyson (7)，hp (7)，best buy (7)
- 上升：mechanic fight warranty claim (5950，污染)，go boult (750)，easton bat (150)，shokz、ray ban、oakley、salomon

`flight delay compensation`

- 头部：compensation for flight delay (100)，eu (62)，uk (48)，airline (31)，claim (30)，canada (26)，india (24)
- 上升：samsung galaxy、导弹、supermoon、wikipedia（污染）。indigo (300) 和 eu flight delay compensation uk (100) 留在航空意图里。

`schengen calculator`

- 头部：schengen visa calculator (100)，days calculator (72)，uk (31)，app (21)，area (14)

`meal plan template`

- 头部：free、pdf、word、weekly、for weight loss

`expense tracker`

- 头部：app (100)，best app (76 / 36)，business (39)，google (37)，template (26)，excel (25)
- 上升：tax refund calculator (45200，污染)，loan calculator (900)，budget planner (300)

`freelance contract`

- 头部：freelance contract jobs (100)，template (36)，upwork (17)，graphic design (11)
- 上升：walmart near me (24750，污染)

`media kit template`、`youtube script template`：相关查询空，或只剩一道营销测验题。

### 税制相关查询

见第 6 节。`form 5472`、`estimated quarterly taxes`、`steuererklärung`、`imposto de renda`、`gst invoice` 的头部查询都落在该国税务机关、申报年份或发票规则上。

## 8. 单独查询仍很小的词

单词地图的 100 只说明「有数据的国家里谁的份额最高」，周均是自身峰值的相对水平，不能和发票模板的 55 比较。和发票模板的比较以第 3 节为准。

| 词 | 自身周均 | 目标国份额 | 指数 ≥15 的前部 |
| --- | ---: | --- | --- |
| upwork proposal | 46.3 | 美 2，英 0，印 4，德 0，巴 0 | PK 100，ET 82，NG 74，KE 61，PH 31，BD 25 |
| schengen calculator | 38.6 | 美 0，英 17，印 0，德 3，巴 0 | XK 100，JE 70，AL 41，MK 41，BA 27，MT 25，ME 25，LT 22，GB 17 |
| freelance invoice | 33.3 | 美 4，英 13，印 0，德 0，巴 0 | 几乎只有低量地区 |
| weekly timesheet | 17.8 | 美 33，英 33，印 0，德 0，巴 0 | NZ 66，AU 33，CA 33 |
| youtube script template | 10.5 | 五个目标国都是 0 | 无实质国家 |
| media kit template | 23.1 | 五个目标国都是 0 | 低量地区 |
| brand deal contract | 13.8 | 五个目标国都是 0 | 低量地区 |
| late payment reminder | 7.8 | 五个目标国都是 0 | 无 |

`upwork proposal` 自身周均 46 只说明它的峰值周被标成 100 之后其余周还不低。它在和退订的同组里是 0.23 对 36。

## 9. 复现

全球 5 年比较的 id：`w_giants`，`w_job`，`w_money`，`w_wedge`，`w_travel`，`w_life`，`w_acad`，`w_docs`，`w_cancel`，`w_exams`，`w_free`，`w_time`，`w_creator`，`w_finalists`，`w_finalists2`。

五国英语比较：`gA_{US,GB,IN,DE,BR}` 与 `gB_{US,GB,IN,DE,BR}`。

本地比较：`l_de`，`l_de2`，`l_br`，`l_in1`，`l_in2`，`l_gb`，`l_us`，`l_fr`，`l_es`，`l_fr2`。

相关查询：`r1` 至 `r7`，加 `r_letters`（motivation letter、cover letter）。

单词对照：`c_estimated_quarterly_taxes`，`c_form_5472`，`c_irmaa`，`c_aca_premium_tax_credit`，`c_property_tax_protest`，`c_self_assessment_tax`，`c_steuererklärung`，`c_imposto_de_renda`，`c_gst_invoice`，`c_student_loan_save_plan`。

周序列存在采集机的原始 JSON 里，没有放进仓库。本文件的周均、月份和比值可以从那些序列重算；上面的表格就是报告引用的全部数字。

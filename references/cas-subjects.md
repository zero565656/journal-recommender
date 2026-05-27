# 中科院学科分类 & LetPub 查询代码

> 说明：`fieldtag` 和期刊数量可能随 LetPub 页面调整而变化。使用时以当前抓取结果为准；期刊数仅帮助估算查询规模，不要作为稳定事实输出给用户。若 `researchfield` 查询为空或异常，回退到 `search` 接口。

## LetPub 研究方向 fieldtag 编号表

LetPub 按研究方向分类，通过 `fieldtag` 数字编号查询：

| 中科院大类 | LetPub 研究方向 | fieldtag | 期刊数 |
|-----------|--------------|----------|--------|
| 计算机科学 | 计算机科学 | 15 | 143 |
| 计算机科学（应用） | 计算机应用技术 | 44 | 54 |
| 工程技术（电气） | 电子学与信息系统 | 21 | 111 |
| 工程技术（机械） | 机械工程 | 22 | 119 |
| 工程技术（自动化） | 自动化 | 23 | 96 |
| 工程技术（电气） | 电气科学与工程 | 43 | 51 |
| 工程技术（土木） | 建筑环境与结构工程 | 24 | 93 |
| 工程技术（综合） | 工程与材料 | 1 | 667 |
| 医学 | 医药科学 | 6 | 230 |
| 生物学 | 生命科学 | 3 | 480 |
| 生物学（微生物） | 微生物学 | 25 | 92 |
| 化学（综合） | 化学科学 | 2 | 566 |
| 化学（分析） | 分析化学 | 17 | 124 |
| 化学（有机） | 有机化学 | 12 | 148 |
| 化学（无机） | 无机化学 | 10 | 162 |
| 化学（催化） | 催化化学 | 30 | 68 |
| 化学（物理） | 物理化学 | 9 | 166 |
| 材料科学 | 金属材料 | 13 | 143 |
| 材料科学（高分子） | 有机高分子材料 | 11 | 154 |
| 材料科学（纳米） | 无机纳米化学 | 33 | 69 |
| 材料科学（半导体） | 半导体材料 | 32 | 67 |
| 环境科学与生态学 | 生态学 | 29 | 73 |
| 数学 | 数学 | 18 | 119 |
| 物理与天体物理 | 物理学I | 14 | 132 |
| 地球科学 | 地球科学 | 8 | 185 |
| 地球科学（地理） | 地理学 | 52 | 66 |
| 地球科学（地质） | 地质学 | 36 | 63 |
| 能源 | 工程热物理与能源利用 | 28 | 83 |
| 管理学 | 管理综合 | 37 | 56 |
| 信息科学（综合） | 信息科学 | 4 | 345 |

---

## 查询 URL 模板

### 按研究方向浏览（推荐，稳定可靠）
```
https://www.letpub.com.cn/index.php?page=journalapp&view=researchfield&fieldtag={fieldtag}&firstletter=
```

### 按关键词搜索 + 大类筛选
```
https://www.letpub.com.cn/index.php?page=journalapp&view=search
&searchname=&searchissn=
&searchfield={大类名称，如 Computer+Science}
&searchcasnewranking={1或2或3或4}
&searchimpactlow={IF下限，可空}
&searchimpacthigh={IF上限，可空}
&page_number=1
```

中科院大类名称（searchfield参数值）：
- 计算机科学 → `Computer Science`
- 医学 → `Medicine`  
- 生物学 → `Biology`
- 工程技术 → `Engineering, Technology`
- 材料科学 → `Materials Science`
- 化学 → `Chemistry`
- 数学 → `Mathematics`
- 物理 → `Physics and Astrophysics`
- 地球科学 → `Earth Sciences`
- 环境科学 → `Environmental Sciences, Ecology`
- 经济学 → `Economics`
- 管理学 → `Management`

---

## 示例查询 URL

### 示例1：计算机科学，查看所有期刊列表
```
https://www.letpub.com.cn/index.php?page=journalapp&view=researchfield&fieldtag=15&firstletter=
```

### 示例2：搜索计算机科学 + 中科院新1区
```
https://www.letpub.com.cn/index.php?page=journalapp&view=search&searchname=&searchissn=&searchfield=Computer+Science&searchcasnewranking=1&page_number=1
```

### 示例3：医学 + 新分区2区 + IF>5
```
https://www.letpub.com.cn/index.php?page=journalapp&view=search&searchfield=Medicine&searchcasnewranking=2&searchimpactlow=5&page_number=1
```

### 示例4：单本期刊详情页（第二层精筛时使用）
```
https://www.letpub.com.cn/index.php?page=journalapp&view=detail&journalid={journalid}
```

---

## 跨学科处理规则

当论文属于多个学科时：
1. **主学科**：单独查询，取全部结果
2. **次学科**（最多2个）：各自查询，取结果
3. **合并**：按期刊名去重，保留来源标注
4. **建议优先用 search 接口**（可同时传分区参数），比 researchfield 更精准

### 常见跨学科组合

| 研究场景 | 主学科 fieldtag | 次学科 fieldtag |
|---------|--------------|--------------|
| AI + 医学影像 | 6（医药科学） | 15（计算机科学） |
| 机器学习 + 金融 | 4（信息科学） | 37（管理综合） |
| 环境污染 + 人体健康 | 29（生态学） | 6（医药科学） |
| 新型电池材料 | 13（金属材料） | 2（化学科学） |
| NLP / 自然语言处理 | 15（计算机科学） | 4（信息科学） |
| 智慧农业 | 3（生命科学） | 23（自动化） |

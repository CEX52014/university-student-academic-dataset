# 高校学生学业数据集

[![License: CC BY-NC-SA 4.0](https://img.shields.io/badge/License-CC%20BY--NC--SA%204.0-lightgrey.svg)](https://creativecommons.org/licenses/by-nc-sa/4.0/)
[![Data Source](https://img.shields.io/badge/Source-University%20System-blue.svg)]()

## 📊 数据集简介

本数据集包含某综合性大学2020-2024学年的学生学业相关数据，经过严格脱敏处理，可用于教育数据挖掘、学业预警、智能推荐等研究。数据来源于高校教务管理系统与在线学习平台，涵盖学生基本信息、课程信息、成绩记录、出勤情况和在线学习行为等多个维度。

### 数据规模

- **学生数量**: 2,001名
- **课程数量**: 132门
- **成绩记录**: 59,511条
- **出勤记录**: 59,511条
- **在线学习日志**: 59,511条
- **时间跨度**: 2020-2024学年

## 📁 数据文件说明

### 1. students.csv - 学生基本信息表

包含学生的基本信息和背景数据，所有敏感信息已脱敏处理。

| 字段名 | 说明 | 示例 |
|--------|------|------|
| student_id | 学生编号（已脱敏） | 2020000001 |
| name | 姓名（已脱敏） | 学生0001 |
| gender | 性别 | 男/女 |
| birth_date | 出生日期 | 2001-04-08 |
| enrollment_year | 入学年份 | 2021 |
| grade | 年级 | 4 |
| college | 学院 | 计算机学院 |
| major | 专业 | 软件工程 |
| class_id | 班级 | 2021计算软件工程01 |
| student_type | 学生类型 | 本科/专升本 |
| political_status | 政治面貌 | 共青团员 |
| province | 生源省份 | 江苏 |
| is_rural | 是否农村生源 | True/False |
| family_economic_status | 家庭经济状况 | 困难/一般/良好 |

### 2. courses.csv - 课程信息表

包含学校开设的各类课程信息。

| 字段名 | 说明 | 示例 |
|--------|------|------|
| course_id | 课程编号 | C001 |
| course_name | 课程名称 | 数据结构 |
| course_type | 课程类型 | 专业必修/公共必修/专业选修/公共选修 |
| credits | 学分 | 3.0 |
| hours | 学时 | 48 |
| college | 开课学院 | 计算机学院 |
| difficulty_level | 难度系数 | 1-5 |
| has_experiment | 是否有实验课 | True/False |

### 3. course_records.csv - 选课成绩记录表

记录学生的选课和成绩信息。

| 字段名 | 说明 | 示例 |
|--------|------|------|
| record_id | 记录ID | 1 |
| student_id | 学生编号 | 2020000001 |
| course_id | 课程编号 | C001 |
| semester | 学期 | 2023-2024-1 |
| teacher_id | 任课教师ID（已脱敏） | T001 |
| usual_score | 平时成绩（30%） | 85.5 |
| midterm_score | 期中成绩（20%） | 82.0 |
| final_score | 期末成绩（50%） | 88.0 |
| total_score | 总评成绩 | 86.1 |
| grade_point | 绩点 | 3.6 |
| is_retake | 是否重修 | False |
| is_makeup | 是否补考 | False |
| rank_in_class | 班级排名 | 15 |

### 4. attendance.csv - 出勤记录表

记录学生的课堂出勤情况。

| 字段名 | 说明 | 示例 |
|--------|------|------|
| attendance_id | 记录ID | 1 |
| student_id | 学生编号 | 2020000001 |
| course_id | 课程编号 | C001 |
| semester | 学期 | 2023-2024-1 |
| total_classes | 总课时数 | 48 |
| attended_classes | 实际出勤 | 45 |
| late_times | 迟到次数 | 2 |
| leave_times | 请假次数 | 1 |
| absent_times | 旷课次数 | 0 |
| attendance_rate | 出勤率 | 0.9375 |

### 5. online_learning.csv - 在线学习行为表

记录学生在线学习平台的行为数据。

| 字段名 | 说明 | 示例 |
|--------|------|------|
| log_id | 日志ID | 1 |
| student_id | 学生编号 | 2020000001 |
| course_id | 课程编号 | C001 |
| date | 日期 | 2024-03-15 |
| login_times | 登录次数 | 3 |
| online_duration | 在线时长（分钟） | 120 |
| video_watch_count | 观看视频数 | 5 |
| video_completion_rate | 视频完成率 | 0.85 |
| forum_post_count | 论坛发帖数 | 2 |
| forum_reply_count | 论坛回复数 | 3 |
| homework_submitted | 作业提交数 | 1 |
| homework_on_time | 按时提交数 | 1 |
| resource_download_count | 资源下载次数 | 4 |

## 🔧 使用方法

### Python 示例

```python
import pandas as pd

# 读取数据
students = pd.read_csv('students.csv')
courses = pd.read_csv('courses.csv')
records = pd.read_csv('course_records.csv')
attendance = pd.read_csv('attendance.csv')
online = pd.read_csv('online_learning.csv')

# 数据探索
print(students.head())
print(students.describe())

# 关联分析
merged_data = records.merge(students, on='student_id')
merged_data = merged_data.merge(courses, on='course_id')
```

### R 示例

```r
# 读取数据
students <- read.csv('students.csv')
courses <- read.csv('courses.csv')
records <- read.csv('course_records.csv')

# 数据探索
summary(students)
head(students)

# 数据关联
merged_data <- merge(records, students, by='student_id')
merged_data <- merge(merged_data, courses, by='course_id')
```

## 📈 应用场景

本数据集可用于以下研究方向：

- ✅ **学业预警系统**: 预测学生学业风险，及早干预
- ✅ **成绩预测**: 基于历史数据预测学生成绩
- ✅ **辅助教学**: 分析教学效果，优化教学策略
- ✅ **学习行为分析**: 挖掘学习模式，个性化推荐
- ✅ **教育数据挖掘**: 探索影响学业表现的关键因素
- ✅ **智能推荐系统**: 课程推荐、学习资源推荐
- ✅ **学习画像构建**: 多维度刻画学生特征

## 🔒 隐私保护

本数据集已进行严格的脱敏处理：

- ✔️ 学生姓名已替换为编号（学生0001、学生0002...）
- ✔️ 学号已重新编码，无法追溯到真实学生
- ✔️ 教师ID已匿名化
- ✔️ 出生日期保留年月日但已作随机调整
- ✔️ 所有数据均已脱离原始系统，无法反向识别个人身份

**数据符合《个人信息保护法》和教育部相关数据安全规范。**

## 📜 引用说明

如果您在研究或项目中使用了本数据集，请注明数据来源：

```
高校学生学业数据集
来源：高校教务管理系统（已脱敏）
采集时间：2020-2024学年
GitHub: https://github.com/CEX52014/university-student-academic-dataset
```

## ⚖️ 许可协议

本数据集采用 [CC BY-NC-SA 4.0](https://creativecommons.org/licenses/by-nc-sa/4.0/) 许可协议：

- ✅ 可以自由使用、修改和分享数据
- ✅ 必须注明原始数据来源
- ⛔ 禁止用于商业用途
- ⛔ 再分发需使用相同协议

## 📧 联系方式

如有数据使用问题或合作意向，欢迎通过以下方式联系：

- 📮 GitHub Issues: https://github.com/CEX52014/university-student-academic-dataset/issues
- 💬 欢迎提交 Pull Request

## 🎯 更新日志

### v1.0.0 (2024-10)
- 初始版本发布
- 包含2020-2024学年数据
- 完成数据脱敏和质量检查

---

**⚠️ 免责声明**: 本数据集仅供学术研究和教学使用，不得用于任何商业目的。数据使用者需自行承担数据使用的法律责任。


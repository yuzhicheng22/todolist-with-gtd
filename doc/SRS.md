# 需求规格说明书（SRS, Software Requirements Specification）

### **1. 项目概述**
#### **1.1 项目目标**
开发一款基于GTD（Getting Things Done）方法的效率类App，专注于时间管理和待办事项处理，降低用户学习成本，以简洁、轻量化的操作界面提升用户工作与学习效率。

#### **1.2 用户需求**
1. **核心需求**：
   - 快速记录和管理任务。
   - 自动化任务分类，减少用户决策负担。
   - 提供任务完成提醒，确保关键事项不被遗忘。
   - 支持复盘功能，帮助用户反思和提升效率。
2. **目标用户**：
   - 自由职业者。
   - 职场白领。
   - 学生群体。

#### **1.3 项目范围**
1. 初版聚焦本地功能：任务管理、提醒、基础复盘。
2. 后续版本可扩展多设备同步、数据可视化和高级功能模块（如番茄工作法、OKR管理）。

---

### **2. 功能需求**

#### **2.1 任务管理模块**
1. **功能描述**：
   - 用户可以新增、编辑、删除、标记任务完成。
   - 提供任务的优先级设定和截止时间功能。
   - 自动化分类任务（如“今天要做”、“稍后做”）。
2. **功能行为**：
   - **新增任务**：
     - 用户点击“+”按钮，输入任务标题、截止时间和优先级，点击保存后，任务显示在任务列表中。
   - **编辑任务**：
     - 用户点击任务项，进入编辑页面，修改后保存即可。
   - **删除任务**：
     - 用户左滑任务，点击删除按钮即可移除。
   - **标记完成**：
     - 用户勾选任务，即任务状态变为“已完成”。
3. **边界条件**：
   - 标题字符限制：最多50个字符。
   - 截止时间：用户不能选择当前时间之前。
   - 最大任务数量：1000条（避免性能问题）。

---

#### **2.2 通知提醒模块**
1. **功能描述**：
   - 根据用户设定的截止时间，发送通知提醒。
   - 支持位置提醒（例如到达某地时提醒完成任务）。
2. **功能行为**：
   - **时间提醒**：
     - 用户设置任务截止时间后，系统在任务到期前15分钟发送通知。
   - **位置提醒**：
     - 用户选择位置，App在用户进入指定地点时触发提醒。
3. **边界条件**：
   - 时间提醒：支持当天或未来7天内的任务提醒。
   - 位置提醒：基于用户授权定位服务，可精度范围为100米。

---

#### **2.3 复盘模块**
1. **功能描述**：
   - 提供任务完成率和未完成任务的统计。
   - 按天/周/月生成复盘报告。
2. **功能行为**：
   - 用户点击“复盘”页面，可查看已完成任务、未完成任务，以及任务完成率。
   - 每周自动生成复盘报告，提示用户查看。
3. **边界条件**：
   - 每日复盘数据自动更新。
   - 复盘数据存储周期：3个月（本地存储有限）。

---

#### **2.4 用户界面**
1. **功能描述**：
   - 主界面展示任务列表。
   - 支持任务的拖动排序。
   - 复盘界面以图表形式展示数据。
2. **功能行为**：
   - 用户可以通过拖拽任务调整优先级。
   - 通过柱状图查看每日任务完成率。
3. **边界条件**：
   - 主界面任务显示最多10条，剩余任务通过分页展示。

---

### **3. 非功能性需求**

#### **3.1 性能需求**
- 页面响应时间：操作任务列表的响应时间不超过300ms。
- 通知准确率：提醒触发成功率≥99%。

#### **3.2 用户体验**
- 界面风格：采用Minimal设计风格，界面清晰、交互直观。
- 操作步骤：所有任务管理功能操作不超过3步。

#### **3.3 安全需求**
- 本地数据加密存储，防止用户隐私泄露。
- 严格遵守iOS隐私权限要求，仅在必要时获取用户位置和通知权限。

---

### **4. 开发限制**
- 支持系统：iOS 15及以上。
- 本地化语言：初期支持简体中文，后续可扩展为多语言。
- 存储限制：App初始包体积控制在50MB以内。

---

### **5. 流程图与操作路径**
- **任务新增流程**：
  1. 用户点击主界面“+”按钮。
  2. 输入任务标题、截止时间、优先级。
  3. 点击保存，任务显示在主界面任务列表中。

- **通知触发流程**：
  1. 用户在任务详情页设置提醒。
  2. 系统定时或基于地理位置条件触发通知。
  3. 用户点击通知，跳转到任务详情页。

---

### **6. 验收标准**
1. 所有功能在符合边界条件的情况下正常运行。
2. 界面布局与用户交互设计符合需求文档描述。
3. 功能测试通过率≥95%。
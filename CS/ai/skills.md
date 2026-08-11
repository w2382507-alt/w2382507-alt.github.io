1. 在skill的文件夹内创建新文件夹，名称即skill的名称
2. SKILL.md文件为说明文档，告诉agent该怎么做
	- 在metadata处按格式编写：
	     \---
	     name: education
		 description: "Generate study plans, quizzes, flashcards, review materials, track learning progress and schedule study sessions. Use when users ask to create study plans, generate quiz questions, make flashcards, track study progress, or schedule review sessions for any topic."
		 description_zh: "学习助手：生成学习计划、测验、抽认卡、复习材料并跟踪进度"
		 description_en: "Study assistant: generate plans, quizzes, flashcards, review materials and track progress"
		 version: 3.4.1
		 homepage: https://clawhub.ai/skills/education
		 allowed-tools: Read,Write,Bash
		 \---
	
	- 下边就正常用自然语言编写提示词
3. reference文件夹内放置被参考的文件，当被SKILL.md要求调用的时候会一并传给大模型
4. script文件夹内放置被执行的文件，当被SKILL.md要求调用时会被agent运行
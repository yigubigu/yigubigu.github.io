---
date: 2017-08-15 09:50:47+00:00
layout: post
title: 'machine learning definition'
categories: 文档
tags:  'machine learning'
---

机器学习是什么？在本视频中，我们会尝试着进行定义，同时 让你懂得何时会使用机器学习。实际上，即使是在 机器学习的专业人士中，也不存在一个被广泛认可的定义 来准确定义机器学习是什么或不是什么，现在我将告诉你 一些人们尝试定义的示例。第一个机器学习的定义来自于Arthur Samuel。 他定义机器学习为，在进行特定编程的情况下， 给予计算机学习能力的领域。Samuel的定义 可以回溯到50年代，他编写了一个西洋棋程序。 这程序神奇之处在于，编程者自己并不是个下棋高手。 但因为他太菜了，于是就通过编程， 让西洋棋程序自己跟自己下了上万盘棋。通过观察 哪种布局（棋盘位置）会赢，哪种布局会输， 久而久之，这西洋棋程序明白了什么是好的布局， 什么样是坏的布局。然后就牛逼大发了，程序通过学习后， 玩西洋棋的水平超过了Samuel。这绝对是令人注目的成果。 尽管编写者自己是个菜鸟，但因为 计算机有着足够的耐心，去下上万盘的棋， 没有人有这耐心去下这么多盘棋。通过这些练习， 计算机获得无比丰富的经验，于是渐渐成为了 比Samuel更厉害的西洋棋手。上述是个有点不正式的定义， 也比较古老。另一个年代近一点的定义，由Tom Mitchell提出，来自卡内基梅隆大学，Tom定义的机器学习是 这么啰嗦的，一个好的学习问题定义如下，他说， 一个程序被认为能从经验E中学习，解决任务 T，达到 性能度量值P，当且仅当，有了经验E后，经过P评判， 程序在处理 T 时的性能有所提升。我认为他提出的这个定义就是为了压韵 在西洋棋那例子中，经验e 就是 程序上万次的自我练习的经验 而任务 t 就是下棋。性能度量值 p呢， 就是它在与一些新的对手比赛时，赢得比赛的概率。 在这些视频中，除了我教你的内容以外， 我偶尔会问你一个问题，确保你对内容有所理解 说曹操，曹操到，顶部是Tom Mitchell的机器学习的定义， 我们假设您的电子邮件程序会观察收到的邮件是否被你标记 为垃圾邮件。在这种Email客户端中，你点击“垃圾邮件”按钮 报告某些email为垃圾邮件，不会影响别的邮件。基于被标记为垃圾的邮件， 您的电子邮件程序能更好地学习如何过滤垃圾邮件。请问， 在这个设定中，任务 T 是什么？几秒钟后，该视频将暂停。当它暂停时， 您可以使用鼠标，选择这四个单选按钮中的一个，让我 知道这四个，你所认为正确的选项。它可能 是性能度量值P。所以，以性能度量值P为标准，这个任务的性能， 也就是这个任务T的系统性能，将在学习经验E后得到提高 本课中，我希望教你有关各种不同类型的 学习算法。目前存在几种不同类型的学习算法。 主要的两种类型被我们称之为监督学习和无监督学习。 在接下来的几个视频中，我会给出这些术语的定义。 这里简单说两句，监督学习这个想法是指，我们将教 计算机如何去完成任务，而在无监督学习中，我们打算让 它自己进行学习。如果对这两个术语仍一头雾水，请不要担心， 在后面的两个视频中，我会具体介绍这两种学习算法。 此外你将听到诸如，强化学习和推荐系统等 各种术语 这些都是机器学习算法的一员，以后我们都将介绍到 但学习算法最常用两个类型就是监督学习、无监督学习 我会在接下来的两个视频中给出它们的定义 本课中，我们将花费最多的精力来讨论这两种学习算法 而另一个会花费大量时间的任务是 了解应用学习算法的实用建议。 我非常注重这部分内容，实际上，就这些内容而言 我不知道还有哪所大学会介绍到。给你讲授学习算法 就好像给你一套工具，相比于提供工具，可能更重要的 是教你如何使用这些工具。 我喜欢把这比喻成学习当木匠。想象一下， 某人教你如何成为一名木匠，说这是锤子，这是 螺丝刀，锯子，祝你好运，再见。这种教法不好，不是吗？ 你拥有这些工具，但更重要的是，你要学会如何恰当地使用 这些工具。会用与不会用的人之间，存在着鸿沟。 尤其是知道如何使用这些机器学习算法的，与那些不知道 如何使用的人。在硅谷我住的地方，当我走访不同的公司， 即使是最顶尖的公司，很多时候我都看到 人们试图将机器学习算法应用于某些问题 有时他们甚至已经为此花了六个月之久。但当我看着 他们所忙碌的事情时，我想说，哎呀，我本来可以 在六个月前就告诉他们，他们应该采取一种学习算法 稍加修改进行使用，然后成功的机会绝对会高得多 所以在本课中，我们要花很多时间来探讨， 如果你真的试图开发机器学习系统， 探讨如何做出最好的实践类型决策，才能决定你的方式 来构建你的系统，这样做的话，当你运用学习算法时，就不太容易变成 那些为寻找一个解决方案花费6个月之久的人们的中一员。 他们可能已经有了大体的框架，只是没法正确的工作 于是这就浪费了六个月的时间。所以我会花 很多时间来教你这些机器学习、人工智能的最佳实践 以及如何让它们工作，我们该如何去做，硅谷和世界各地 最优秀的人是怎样做的。我希望能帮你成为最优秀的人才， 通过了解如何设计和构建机器学习和人工智能系统。 这就是机器学习，这些都是我希望讲授的主题。在下一个 视频里，我会定义什么是监督学习， 什么是无监督学习。此外，探讨何时使用二者。
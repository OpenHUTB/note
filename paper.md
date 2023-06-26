


BTN选期刊：

NATURE NEUROSCIENCE
35.30
http://www.letpub.com.cn/index.php?journalid=6066&page=journalapp&view=detail

NEURON：
http://www.letpub.com.cn/index.php?journalid=6169&page=journalapp&view=detail
25.30

TRENDS IN NEUROSCIENCES
http://www.letpub.com.cn/index.php?journalid=7927&page=journalapp&view=detail
18.60

NEUROIMAGE
http://www.letpub.com.cn/index.php?journalid=6150&page=journalapp&view=detail
10.60

JOURNAL OF NEUROSCIENCE
http://www.letpub.com.cn/index.php?journalid=4909&page=journalapp&view=detail
10.30

PLoS Computational Biology
http://www.letpub.com.cn/index.php?journalid=6771&page=journalapp&view=detail
7.30

NeuroImage-Clinical
http://www.letpub.com.cn/index.php?journalid=9881&page=journalapp&view=detail
7.00

BIOINFORMATICS
http://www.letpub.com.cn/index.php?journalid=1122&page=journalapp&view=detail
9.90



PLoS Computational Biology
http://www.letpub.com.cn/index.php?journalid=6771&page=journalapp&view=detail
7.30

IEEE-ACM Transactions on Computational Biology and Bioinformatics
http://www.letpub.com.cn/index.php?journalid=3431&page=journalapp&view=detail
6.40


筛选出：
JOURNAL OF NEUROSCIENCE
http://www.letpub.com.cn/index.php?journalid=4909&page=journalapp&view=detail

TRENDS IN NEUROSCIENCES
http://www.letpub.com.cn/index.php?journalid=7927&page=journalapp&view=detail

PLoS Computational Biology
http://www.letpub.com.cn/index.php?journalid=6771&page=journalapp&view=detail





JDAN

亲爱的同事，

我收到了关于您提交给 TOMM 的评论，题为“JDAN：实时在线多目标跟踪的联合检测和关联网络”。根据审稿人的意见，论文需要经过重大修改后才能考虑在TOMM上发表。审稿人的详细评论附在本电子邮件的末尾。
一旦您修改了您的论文，请通过 TOMM 论文提交系统 https://mc.manuscriptcentral.com/tomm 重新提交您的手稿（pdf 或 ps），点击“Revised Manscripts”，然后点击您要上传的手稿的标题的修订。您应该使用文件类型“主文件”。请确保您的手稿使用小型 ACM 期刊格式 (http://www.acm.org/pubs/submissions/submission.htm) 严格限制在 23 页以内。
同时上传您的修订评论（pdf 或 ps 格式），详细说明您对论文所做的更改以回应审稿人的评论。请确保使用“其他”文件类型。您的修订应自本电子邮件日期（2021 年 12 月 10 日）起八 (8) 周到期。
您修改后的论文和评论将由您论文的原始审稿人进行审核，以查看他们的疑虑是否已得到解决。



审稿人意见
裁判：1
建议：需要小修改

注释：
他的论文提出了一种端到端的检测结构，以从视频中实现目标跟踪任务。它首先利用现有的物体检测方法和相关的关联方法来设计所提出结构的子模块。然后将这些子模块与传统的关联方法相结合，生成视频中的对象轨迹。最后，它分析当前帧和历史帧的对象表示及其轨迹，以提高多对象跟踪性能。在两个不同的 MOT 基准上的实验结果证明了所提出方法的有效性。
1、图的乱序影响阅读。
2.在贡献一中，它声称所提出的结构是一种端到端的方法，但论文似乎将该方法分为2个阶段？
3. 结果是从当前帧和历史帧计算出来的。因此，它如何影响检测过程的速度？能不能分析一下这个方法和其他比较方法的FPS或者肤色？

附加问题：
审稿人推荐的论文类型：全长技术论文
这篇论文是否应该被考虑获得最佳论文奖？：否
这篇论文是否提出了创新的想法或材料？：是的
本文在哪些方面推动了该领域的发展？：
论文中的信息是否可靠、真实和准确？：是
如果不是，请解释原因。：

论文的主要贡献有哪些？： 1.本文方法描述清晰，易于理解。
2. 实验结果似乎不错，尤其是在 MOT17 上。
评价想法的表达效果（非常难理解=1 非常容易理解=5:4
评价写作的整体质量（非常差=1，优秀=5：4
本文是否引用并使用了适当的参考文献？：是
如果没有，缺少哪些重要的参考资料？：
是否应该从论文中删除或浓缩任何内容？：否
如果是这样，请解释。：
对象的治疗是否完成？：是
如果没有，缺少哪些重要的细节/想法/分析？：
请帮助 ACM 创建一个更有效的发布时间流程：根据您的最佳判断，您认为这篇论文需要多少副本编辑？：Light
大多数 ACM 期刊论文都是面向研究人员的。开发人员和工程师对这篇论文有潜在的兴趣吗？：也许



裁判：2

建议：需要大修

注释：
这份手稿研究了使用单阶段模型进行检测和关联的对象跟踪问题。具体来说，作者使用额外的检测损失修改 DLA 并在阶段 1 中对其进行训练，然后他们固定检测模块的参数，并在阶段 2 中使用相关损失对模型进行微调。 整体结构与两阶段不同模型和联合训练的单阶段模型，因此可以被视为一种中间选择。以下是我对此提交的担忧。
(1).第 2 页，第 30-40 行描述了现有单级跟踪器的两个问题。第一个是“检测和关联任务之间的模态差异”，是否有任何参考或实验结果来支持这一说法使其合理？第二个是“MOT的检测结果没有相应的检测模型实现”，这让我很困惑。这是否意味着检测模型的类别来自另一个数据集，而不是来自 MOT？
(2) 第 3 页，第 32 行，“首先在训练阶段 1 中训练我们的检测子模块”在哪个数据集上？第 33 行“并利用传统关联方法产生轨迹”，请说明“传统方法”指的是什么。第 45 行，“我们设计了一个端到端的架构”。 “端到端”的含义不同于传统的联合训练工作。由于这项工作是针对两个任务在两个单独的阶段进行训练的，因此会带来不准确性。
(3) 第 5 页，第 40-41 行“这些修改同样有利于缓解对齐问题”。是否有实验结果支持对 DLA 的修改带来了对原始 DLA 的改进？
（4）第8页第20行“首先，我们使用预训练的检测子模块和传统关联”，请注明“传统关联”
(5) 第15页第4-23行表4，作者只与两级跟踪器进行了比较，为什么不在此表中列出其他单级模型？
(6).第16页，表6，作者提到了几个单阶段模型TrackRCNN、JDE、FairMot（在第17页第13-14行提到），但只比较了一个JDE，为什么不涉及其余的。顺便说一下，最好将表 4 和表 6 结合起来。
(7).编辑问题：第 15 页第 50 行，请注明“表 ??”

附加问题：
审稿人推荐的论文类型：全长技术论文
这篇论文是否应该被考虑获得最佳论文奖？：否
这篇论文是否提出了创新的想法或材料？：是的
本文在哪些方面推进了该领域？：手稿提供了两阶段和一阶段跟踪模型之间的替代方法，即使用一个经过两步策略训练的主干。具体来说，他们首先应用检测损失，然后应用关联损失。总体而言，该机制适用于实验结果。
论文中的信息是否可靠、真实和准确？：是
如果不是，请解释原因。：
论文的主要贡献是什么？：主要贡献在于：使用主干在两步训练策略下实现目标检测和身份关联。针对这个目标，在 DLA 之上修改对象检测损失并引入新的身份关联损失。
评价想法的表达效果（非常难理解=1 非常容易理解=5:3
评价写作的整体质量（非常差=1，优秀=5：3
本文是否引用并使用了适当的参考文献？：是
如果没有，缺少哪些重要的参考资料？：
是否应该从论文中删除或浓缩任何内容？：否
如果是这样，请解释。：
对象的治疗是否完成？：是
如果没有，缺少哪些重要的细节/想法/分析？：
请帮助 ACM 创建一个更有效的发布时间流程：根据您的最佳判断，您认为这篇论文需要多少副本编辑？：中等
大多数 ACM 期刊论文都是面向研究人员的。开发人员和工程师对这篇论文有潜在的兴趣吗？：也许


裁判：3
建议：需要大修
注释：
本文提出了一种使用联合检测和关联网络 (JDAN) 的单阶段多目标跟踪方法。该方法在 MOT15 和 MOT17 数据集上进行评估。显示了对现有基线的一些改进。但是，本文的介绍需要大量修改。目前的写作使得很难有效地评估想法的新颖性、技术的合理性和实验的完整性。例如：
(1) FairMOT [58] 和 JDE [60] 是最近提出的单阶段 MOT 方法，它们与提出的 JDAN 非常相关。与这些方法相比，JDAN 的主要区别是什么？此外，这些差异如何或为什么可以帮助 JDAN 更好地应对 MOT 中的挑战？ “真正的端到端”具体是什么意思？这些必须在论文中进一步澄清，以使贡献更加清晰。
(2) Section 3 的组织有点乱。可能缺少概述文本或图形来概括所有内容。图2、图3、图4之间的关系不明确，小节与图的对应关系也不清楚。此外，建议在第 3 节中突出 JDAN 的新颖部分，而将更多现有实现留在第 4.2 节中。
(3) 在实验中，应该对现有的方法以及选择或不选择它们的原因进行一些简短的描述。特别是，为什么没有比较 FairMOT [58]？而且，作者应该更多地解释 JDAN 在表 4 和表 6 中的某些指标下的较差性能。

其他详细评论：
(1) 为了验证 JDAN 的优越性，作者可以考虑 [R1] 中使用的 VidOR 基准数据集。
(2) 论文中从未使用表 7。如果未在某处提及，作者应将其删除。
(3) 请仔细检查公式 4，它似乎缺少一个负号。
(4) 在摘要中，作者提到生成了一个合适的训练数据集来解决不一致问题。这是本文的贡献吗？这篇论文应该更多地讲述它。
[R1] Luo, Z.、Zhang, Z. 和 Yao, Y.（2020 年 10 月）。 VidOR 数据集上多对象跟踪的强大基线。第 28 届 ACM 国际多媒体会议论文集（第 4595-4599 页）。

附加问题：
审稿人推荐的论文类型：全长技术论文
这篇论文是否应该被考虑获得最佳论文奖？：否
这篇论文是否提出了创新的想法或材料？：
本文在哪些方面推动了该领域的发展？：
论文中的信息是否可靠、真实和准确？：
如果不是，请解释原因。：
论文的主要贡献是什么？：
评价想法的表达效果（非常难理解=1 非常容易理解=5:2
评价写作的整体质量（非常差=1，优秀=5：2
本文是否引用并使用了适当的参考文献？：
如果没有，缺少哪些重要的参考资料？：
是否应该从论文中删除或浓缩任何内容？：
如果是这样，请解释。：
对象的处理是否完成？：
如果没有，缺少哪些重要的细节/想法/分析？：
请帮助 ACM 创建一个更有效的发布时间流程：根据您的最佳判断，您认为这篇论文需要多少副本编辑？：Heavy
大多数 ACM 期刊论文都是面向研究人员的。开发人员和工程师对这篇论文有潜在的兴趣吗？：也许





Dear colleague,

I have received the reviews on your submission to TOMM entitled "JDAN: Joint Detection and Association Network for Real-Time Online Multi-Object Tracking".  On the basis of the reviewers' comments, the paper should undergo major revisions before it can be considered for publication in TOMM.  Detailed comments from the reviewers are appended to the end of this email.

Once you have revised your paper, please resubmit your Manuscript (pdf or ps) through TOMM paper submission system at https://mc.manuscriptcentral.com/tomm by clicking on Revised Manscripts and then on the title of the manuscript that you are uploading the revision for. You should use the file type "Main file". Please ensure that your manuscript stays within the strict limit of 23 pages using the small ACM journal format (http://www.acm.org/pubs/submissions/submission.htm).

Also upload your Revision Comments (in pdf or ps) that detail the changes you made to your paper in response to reviewers' comments.  Please ensure to use the file type "Other".  Your revision is due eight (8) weeks from the date on this email (10-Dec-2021).

Your revised paper and comments will be reviewed by your paper's original reviewers to see if their concerns have been addressed.


Best regards,

Dr Yu-Gang Jiang
Associate Editor, ACM TOMM

Reviewer's comments
Referee: 1

Recommendation: Needs Minor Revision

Comments:
his paper proposes an end-to-end detection structure to achieve the object tracking task from a video. It first exploits the existing object detection methods and related association methods to the design sub-modules of the proposed structure. Then it combines these sub-modules with the traditional association methods to generate the object trajectories in the video. Finally, it analyzes the object representations and their trajectories of the current frame and historical frames to improve the multi-object tracking performance. The experimental results on two different MOT benchmarks, demonstrate the effectiveness of the proposed methods.

1. The disorder of the Figures affects the paper reading.
2. In contribution one, it claims the proposed structure is an end-to-end method, but the paper seems to write the method into 2 stages?
3. The results are calculated from the current frame and historical frames. Thus, how does it influences the speed of the detection process? Can analyze the FPS or complexion between this method and other comparison methods?

Additional Questions:
Review's recommendation for paper type: Full length technical paper

Should this paper be considered for a best paper award?: No

Does this paper present innovative ideas or material?: Yes

In what ways does this paper advance the field?:

Is the information in the paper sound, factual, and accurate?: Yes

If not, please explain why.:

What are the major contributions of the paper?: 1. The descriptions of the method in this paper are clear, and the method is easy to follow.
2. The experimental results seem good, especially on the MOT17.

Rate how well the ideas are presented (very difficult to understand=1 very easy to understand =5: 4

Rate the overall quality of the writing (very poor=1, excellent=5: 4

Does this paper cite and use appropriate references?: Yes

If not, what important references are missing?:

Should anything be deleted from or condensed in the paper?: No

If so, please explain.:

Is the treatment of the subject complete?: Yes

If not, What important details / ideas/ analyses are missing?:

Please help ACM create a more efficient time-to-publication process: Using your best judgment, what amount of copy editing do you think this paper needs?: Light

Most ACM journal papers are researcher-oriented. Is this paper of potential interest to developers and engineers?: Maybe


Referee: 2

Recommendation: Needs Major Revision

Comments:
This manuscript studies the problem of object tracking with a single-stage model doing detection and association together. Specifically, the authors modify DLA with extra detection loss and train it in phase 1, then they fix parameters of the detection module, and fine-tune the model with the associated loss in phase 2.  The overall structure is different from both two-stage models and joint-trained one-stage models, thus can be treated as a middle alternative. Below are my concerns regarding this submission.
(1). Page 2, line 30-40 describes two problems of existed one-stage tracker. The first one is "modality difference between detection and association task", is there any reference or experimental results to support this claim to make it sound?  The second one is "detection results of MOT have no corresponding detection model implementation", whichi confuses me. Does it means that the category of detection model is from another dataset, not on MOT?

(2) Page 3, line 32, "first train our detection submodule in training stage 1" on which dataset? line 33 "and utilize traditional association method to produce trajectories", please clarify what  "traditional method" is reffering to. line 45, "We design an end-to-end architecture". The meaning of "end-to-end" is different from a conventional expression which refers a joint training work. Since this work is trained in two separate phases for two tasks, this brings inaccuracy.

(3) Page 5, line 40-41 "These modifications are likewise beneficial to relieve the alignment problem". Are there any experimental results to support that the modification on DLA brings improvement over the original DLA?

(4) Page 8, line 20. "First, we use the pre-trained detection submodule and a traditional association", please specify "tradtional association"

(5) Page 15, line 4-23 Table 4, the author only compares with the two-stage trackers, why not presents the other single-stage models in this Table?

(6). Page 16, Table 6, The author mentioned several single-stage models TrackRCNN, JDE, FairMot (mentioned in Page 17, line 13-14), but only compare one JDE, why not involves the rest. By the way, it's better to combine Table 4 and Table 6.

(7). Edit problem: page 15 line 50, please specify "Table ??"

Additional Questions:
Review's recommendation for paper type: Full length technical paper

Should this paper be considered for a best paper award?: No

Does this paper present innovative ideas or material?: Yes

In what ways does this paper advance the field?: The manuscript provides an alternative way between two-stage and one-stage tracking models, namely using one backbone trained with a two-step strategy. Specifically, they first apply detection loss then association loss. Overall, the mechanism worked with experiments results.

Is the information in the paper sound, factual, and accurate?: Yes

If not, please explain why.:

What are the major contributions of the paper?: The major contributions lie in: use a backbone to achieve both object detection and identity association under a two-step training strategy. Towards this target, the modify object detection loss on top of DLA and introduce new identity association losses.

Rate how well the ideas are presented (very difficult to understand=1 very easy to understand =5: 3

Rate the overall quality of the writing (very poor=1, excellent=5: 3

Does this paper cite and use appropriate references?: Yes

If not, what important references are missing?:

Should anything be deleted from or condensed in the paper?: No

If so, please explain.:

Is the treatment of the subject complete?: Yes

If not, What important details / ideas/ analyses are missing?:

Please help ACM create a more efficient time-to-publication process: Using your best judgment, what amount of copy editing do you think this paper needs?: Moderate

Most ACM journal papers are researcher-oriented. Is this paper of potential interest to developers and engineers?: Maybe


Referee: 3

Recommendation: Needs Major Revision

Comments:
This paper proposes a one-stage multi-object tracking approach using a joint detection and association network (JDAN). The approach is evaluated on MOT15 and MOT17 datasets. Some improvements over the existing baselines are shown. However, the presentation of this paper needs much revision. The current writing makes it hard to effectively evaluate the novelty of the idea, technical soundness, and the completeness of the experiments. For example:
(1) FairMOT [58] and JDE [60] are the recently proposed one-stage MOT approaches, which are very related to the proposed JDAN. Compare to these approaches, what are the main differences of JDAN? Also, how or why can those differences help JDAN better address the challenges in MOT? What does “true end-to-end” mean specifically? These must be further clarified in the paper, such that the contributions clearer.
(2) The organization of Section 3 is a bit messy. There may lacks an overview text or figure to wrap up everything. The relations between Figures 2, 3, and 4 are unclear, as well as the correspondence between the subsections and the figures. Besides, it is recommended to highlight the novel parts of JDAN in Section 3 while leave more existing implementations into Section 4.2.
(3) In the experiments, there should be some short descriptions about the existing approaches and the reasons why they are chosen or not chosen. In particular, why is FairMOT [58] not compared? And, the authors should explain more on the inferior performance of JDAN under some metrics in Table 4 and 6.

Other detailed comments:
(1) To validate the superiority of JDAN, the authors may consider the VidOR benchmark datasets as used in [R1].
(2) Table 7 is never used in the paper. If not referred somewhere, the authors should remove it.
(3) Please double check Equation 4, which seems missing a negative sign.
(4) In the abstract, the authors mention that a suitable training dataset is generated to address the inconsistency. Is this a contribution of this paper? The paper should tell about it more.


[R1] Luo, Z., Zhang, Z., & Yao, Y. (2020, October). A Strong Baseline for Multiple Object Tracking on VidOR Dataset. In Proceedings of the 28th ACM International Conference on Multimedia (pp. 4595-4599).

Additional Questions:
Review's recommendation for paper type: Full length technical paper

Should this paper be considered for a best paper award?: No

Does this paper present innovative ideas or material?:

In what ways does this paper advance the field?:

Is the information in the paper sound, factual, and accurate?:

If not, please explain why.:

What are the major contributions of the paper?:

Rate how well the ideas are presented (very difficult to understand=1 very easy to understand =5: 2

Rate the overall quality of the writing (very poor=1, excellent=5: 2

Does this paper cite and use appropriate references?:

If not, what important references are missing?:

Should anything be deleted from or condensed in the paper?:

If so, please explain.:

Is the treatment of the subject complete?:

If not, What important details / ideas/ analyses are missing?:

Please help ACM create a more efficient time-to-publication process: Using your best judgment, what amount of copy editing do you think this paper needs?: Heavy

Most ACM journal papers are researcher-oriented. Is this paper of potential interest to developers and engineers?: Maybe


# 面上项目评审
2-3个A，3-4个B，其他C和D
2A,4B,4C,3D
## 1_6227070746，基于Airkiss技术的嵌入式无线智能家居系统开发与应用
D 
### 新颖性
该申请项目的研究方案主要基于现有理论与技术，主要以Airkiss技术无线通信技术为基础实现低成本高效率的智能家居系统设计，研究目标与技术路线不具有特别的新颖性与独特性。

### 贡献
该申请项目所关注问题，包括能家居系统硬件的可靠性设计技、智能人机交互等，具有一定的科学价值。但是，其中部分关注问题，如Airkiss无线网络终端开发应用设计、系统外围硬件的驱动技术等，不具有很高的科学价值。

### 基础与可行性
申请人及其团队的研究基础主要集中在应用技术层面，基础研究成果较少，有待于进一步提升。项目研究方案主要围绕具体应用与工程技术展开，没有很好地回答有价值的科学问题，有待于进一步完善。

### 其他建议
建议项目团队进一步凝练有价值的科学问题，加强前期研究，提升研究基础，完善研究方案。

## 2_6227071502，移动智能哨岗及关键技术研究
C
### 新颖性
该申请项目的研究方案主要目标是基于智能分析算法和响应的软硬件开发一套移动智能哨岗系统，研究目标在工程上具有一定的新颖性和独创性。

### 贡献
该申请项目所关注问题，比如视频智能分析算法等，具有一定的科学价值。但是，其中大部分关注问题，如哨兵值岗管理系统、移动哨兵值岗一体机、哨兵值岗管理终端、等，不具有很高的科学价值。

### 基础和可行性
申请人及其团队的研究基础主要集中在应用技术的实现层面，基础研究成果较少，有待于进一步提升。项目的研究方案主要围绕具体应用与工程技术展开，没有很好地回答有价值的科学问题，并且所提出的方案过于笼统，有待于进一步完善。

### 其他建议
建议项目团队进一步凝练有价值的科学问题，加强前期研究，提升研究基础，细化和改进研究方案。


## 3_6227071879，石化旋转机械性能退化与剩余寿命预测方法研究
B
### 新颖性
该申请项目的研究方案主要针对石化企业运行安全性问题的需求，研究石化旋转机械性能退化和剩余预测方法，对实际应用有很好地支撑作用，该研究目标在科研和和工程上具有较好的新颖性和独创性。

### 贡献
该申请项目所关注问题，比如石化旋转机械运行特征数据表示、基于数据驱动的性能退化建模和基于LSTM的健康状况评估和剩余寿命预测等，具有一定的科学价值与工程应用价值。

### 基础和可行性
申请人及其团队拥有一定的石化企业研究背景和相关技术方案的研究基础，并且较好地提出该领域的相关科学问题并提出合理的解决方案，具有较好地研究基础和项目可行性。

### 其他建议
建议项目团队在项目实施过程中凝练其他有价值的科学问题，解决实际生产中存在的关键科学问题，牵引该领域的研究发展。



## 4_6227073072，应急场景中自治无人机的协同决策研究
B
### 新颖性
该申请项目主要研究利用智能认知新方法进行无人机应急场景中的智能推理的协同决策，释放操作员的工作压力，研究目标在科学研究和工程上具有一定的新颖性和独创性。

### 贡献
该申请项目所关注问题，比如可解释的视觉场景智能认知方法、基于智能推理的态势感知模型、应急响应中任务驱动的协同决策框架等，具有较好地科学研究价值。

### 基础和可行性
申请人及其团队的研究基础和研究成果一般，但项目的研究方案主要解决了行业急需的一些问题，较好地回答有价值的科学问题，并且提出一系列合理的解决方案。

### 其他建议
建议项目团队进一步加强各个研究内容之间的联系，细化和改进研究方案。



## 5_6227073107，舰载无人装备的人机共融运动规划方法研究
B
### 新颖性
该申请项目主要针对现行以人为主的作业方式在舰载机高峰出动模式下，存在人员易疲劳、不确定性等问题，主要研究舰载“无人装备”的人机共融运动规划技术，研究目标在科学研究和工程上具有一定的新颖性和独创性。

### 贡献
该申请项目所关注问题，比如动态开放场景中基于视觉感知的端到端任务分配与路径生成方法、自适应学习奖励函数的多智能体策略学习算法、智能辅助决策算法等，具有一定的科学研究价值。

### 基础和可行性
申请人及其团队的研究基础和研究成果较好，而且项目的研究方案主要解决了行业急需的一些问题和挑战，较好地凝练了有价值的科学问题，并提出一系列合理的解决方案。

### 其他建议
建议项目团队进一步探索各个研究内容之间的联系并扩展其他有益的探索，细化和改进研究方案。


## 6_6227073215，复杂环境群智推理及协同决策方法研究

A 
### 新颖性
该申请项目主要研究复杂环境下的智能推理与协同决策，同时保证高效、精准地对决策任务进行推理和判断，同时具备协同决策能力，保障任务稳定有序完成。研究目标在科学研究和工程上具很好的新颖性和独创性。

### 贡献
该申请项目研究并突破复杂任务环境下的智能推理与决策关键技术，比如复杂环境下的智能推理和策略迁移方法、多智能体自主组合选择及协同决策方法、协同对抗策略自我调整学习与优化方法，具有很好的科学研究价值。

### 基础和可行性
申请人及其团队的研究基础和研究成果好，而且项目的研究方案主要解决了复杂环境的智能推理与协同决策的许多问题和挑战，很好地凝练了有价值的科学问题，并提出一系列合理的解决方案。

### 其他建议
建议项目团队在研究的基础上进一步探索细化和改进研究方案并考虑算法的实际应用。






## 7_6227073387，基于多智能体强化学习的低碳韧性城市交通拥堵疏解方法研究
B
### 新颖性
该申请项目主要研究利用大数据解决城市交通拥堵所导致的出行成本上升、环境污染加剧等已经成为阻碍我国城市发展和“双碳”目标实现的突出问题。研究基于时空关联的城市交通流量数据补全和城市路网交通流量关联与权重分析方法和研究基于多智能体强化学习的城市交通拥堵疏解方法，该研究目标在科学研究和工程上具有一定的新颖性和独创性。

### 贡献
该申请项目所关注问题，比如时空数据的补全与预测方法、网络结构关联与数据权重分析方法、多智能体协同控制方法等，具有一定的科学研究价值。

### 基础和可行性
申请人和其所在团队的研究基础和研究成果较好，而且项目的研究方案主要解决了行业急需的一些问题和挑战，凝练了一些有价值的科学问题，并提出一系列合理的解决方案。

### 其他建议
建议项目团队进一步探索各个研究内容和国内实际交通场景的结合，优化和改进研究方案。

## 8_6227073449，面向助老陪护机器人的混合增强智能关键技术
C
### 新颖性
该申请项目的研究主要针对当前陪护机器人的任务训练与技能学习，因泛化能力不足的问题，旨在探索一种陪护对象在机器人陪护作业中的监督与指导模式与方法，以提升陪护机器人的适应能力，改善助老陪护机器人的用户体验，为老龄化社会提供技术服务。但是该研究目标与技术路线不具有特别的新颖性与独特性。

### 贡献
该申请项目所关注问题，包括基于隐私保护的依赖陪护对象的多模态认知交互;人监督下的机器人强化学习模型与算法等，具有一定的科学价值。但是，其中部分关注问题，如物品递送任务中混合增强智能陪护机器人应用验证、人指导下的陪护机器人分层学习模型与算法等，不具有很高的科学研究价值。

### 基础与可行性
申请人及其团队的研究基础主要集中在概念层面，基础研究成果较少，有待于进一步提升。项目研究方案主要围绕具体应用与工程技术展开，没有很好地回答有价值的科学问题，有待于进一步完善方案。

### 其他建议
建议项目申请人和团队进一步细化项目中提到的技术方案，加强前期研究，提升研究基础。

## 9_6227073649，可穿戴外骨骼的人机协同控制方法研究
C
### 新颖性
该申请项目的研究方案主要目标是实现复杂变化模式下的人机协同控制，解决我国人工老龄化过程中存在的挑战和难题，研究目标在工程上具有一定的新颖性和独创性。

### 贡献
该申请项目所关注问题，比如对比学习引导的低资源语音关键特征挖掘、多源语言共性知识提取与高效迁移机制和基于度量空间的元学习低资源语音识别方法研究等，具有一定的科学价值。但是，其中大部分关注问题，如人体手势识别实现、外骨骼建模难等，不具有很高的科学价值。

### 基础和可行性
申请人及其团队的研究基础主要集中在应用技术的实现层面，基础研究成果较少，有待于进一步提升。项目的研究方案主要围绕具体应用与工程技术展开，没有很好地回答有价值的科学问题，并且所提出的方案过于抽象和笼统，有待于进一步改善和提高。

### 其他建议
建议项目团队进一步找到有挑战的瓶颈和有价值的科学问题，加强前期研究，提升研究基础，细化和改进研究方案。

## 10_6227073797，基于蜂群协作机理的多微型扑翼飞行机器人集群行为控制方法研究
D
### 新颖性
该申请项目的研究方案主要基于现有理论与方法，主要利用仿生学机理对群体智能进行建模，以期提高仿生群体智能机理，研究目标与技术路线具有一些新颖性与独特性。

### 贡献
该申请项目所关注问题，包括基于行为的方法对蜂群协作进行建模等，具有一定的科学价值。但是，其中部分关注问题，如A对扑翼飞行机器人集群进行建模和实验研究等，不具有很高的科学价值。

### 基础与可行性
申请人及其团队的研究基础主要集中在应用技术层面，基础研究成果不足，有待于进一步提升。项目研究方案主要围绕抽象的概念与工程技术展开，没有很好地回答具体的有价值的科学问题，有待于进一步提高。

### 其他建议
建议项目团队进一步凝练有价值的科学问题，强化前期研究，提升基础研究基础，完善研究方案的可行性。

## 11_6227074289，基于实景数据驱动与自然交互对抗的智能汽车高保真度仿真测试方法研究
C
### 新颖性
该申请项目的研究方案主要解决当前仿真测试方法存在难以建模复杂交通参与者动态行为的随机性、生成的测试案例与自然场景差异较大等问题，研究目标在工程上具新颖性和独创性一般。

### 贡献
该申请项目所关注问题，比如基于深度学习对多模态实景数据进行前后景对象分离，利用对抗生成网络构建组合神经辐射场等，具有一定的科学价值。但是，其中大部分关注问题，如利用自然冲突事件数据库，构建基于高斯混合模型的自然冲突事件模型，实现自然对抗测试场景生成等，不具有很高的科学价值。

### 基础和可行性
申请人及其团队的研究基础主要集中在技术应用的实现层面，基础研究成果较少，有待于进一步提升。项目的研究方案主要围绕具体应用与工程技术展开，没有很好地回答有价值的科学问题，并且所提出的方案过于工程化，有待于进一步完善和提高。

### 其他建议
建议项目团队进一步凝练有价值的科学问题，提升研究基础，加强前期研究，细化和改进研究方案。


## 12_6227074945，刚-柔-软一体化护理机器人的感知与控制方法研究
A
### 新颖性
该申请项目主要研究主动安全性与被动安全性在养老助残与医疗护理等方面的应用前景，研究目标在科学研究和工程上具很好的新颖性和独创性。

### 贡献
该申请项目研究并突破刚-柔-软一体化护理机器人的建模与柔顺控制、任务约束下的机械臂避障运动学、遮挡与变形物体的识别与抓取等方面的关键理论及方法，具有很好的科学研究价值。

### 基础和可行性
申请人及其团队的研究基础和研究成果好，而且项目的研究方案主要解决了护理机器人的主动与被动安全性的许多问题和挑战，很好地凝练了有价值的科学问题，并提出一系列合理的解决方案。

### 其他建议
建议项目团队在研究的基础上进一步探索细化和改进研究方案并考虑项目成果的实际应用。

## 13_6227075001，基于区块链的分布式能源优化调度方法研究
D
该申请项目的研究方案主要研究分布式能源的调度策略及调度方法，主要基于区块链的智能合约和共识机制，研究相应方法的构建与实现，研究目标与技术路线不具有特别的新颖性与独特性。

### 贡献
该申请项目所关注问题，包括能多边交易机制、动态事件触发机制等，具有一定的科学价值。但是，其中部分关注问题，如分布式能源调度模型、动态调度优化算法等，不具有很高的科学价值。

### 基础与可行性
申请人及其团队的研究基础主要集中在应用技术层面，基础研究成果较少，有待于进一步提升。项目研究方案主要围绕具体应用技术展开，没有很好地回答有价值的科学问题，有待于进一步完善和提高。

### 其他建议
建议项目团队进一步凝练有价值的科学问题，加强前期研究，提升研究基础，完善研究方法和思路。

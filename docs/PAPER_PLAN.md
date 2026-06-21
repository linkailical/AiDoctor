# Paper Plan — Tool/System Paper

> Goal: turn the open-source toolkit (browser annotation tool + AI Doctor + dental
> dataset module) into a **systems/tools paper** with a **usability evaluation**,
> suitable for a US student research venue.
> 目标：把这套开源工具做成"系统/工具类论文"，配一次可用性评估，投美国学生科研渠道。

---

## 1. Working titles / 标题候选

1. *An Offline, Zero-Install Web Toolkit for Medical-Image Annotation and Health
   Literacy: Design and Usability Evaluation*
2. *Browser-Based Medical Image Annotation with COCO/YOLO Export for Low-Resource
   and Educational Settings*
3. *AI Doctor & a Lightweight Annotation Tool: Open Web Tools for Teaching Medical AI*

## 2. The contribution / 论文贡献（审稿人想看的"新意"）

Not a new algorithm — the contribution is the **system + evidence it is usable**:

- **Zero-install, fully client-side** (privacy-preserving: images never leave the
  browser) annotation tool with **bounding boxes + polygons, zoom/pan**, and export
  to **standard COCO and YOLO** formats.
- A **bilingual (EN/中文)**, offline, rule-based triage demo (**AI Doctor**) for
  health-literacy education, with explicit safety disclaimers.
- An **extensible, openly-licensed dental image dataset module**.
- A **usability study** showing students can produce usable annotations quickly.

> 关键：贡献=可用的开源系统 + 评估证据（隐私保护、零安装、标准格式导出、双语科普）。

## 3. Structure (IMRaD) / 结构

1. **Introduction** — annotation tools are often heavy / require install / raise
   privacy concerns; health literacy gap. List 3–4 contributions.
2. **Related Work** — LabelImg, CVAT, Label Studio (annotation); online symptom
   checkers; educational medical-AI tools. Position ours as offline/zero-install/edu.
3. **System Design** — architecture (single-page, no backend); annotation tool
   (interaction, coordinate model, COCO/YOLO export); AI Doctor rule engine; dataset
   module; design goals (offline, zero-install, bilingual, privacy, extensible).
4. **Evaluation Methods** — participants, tasks, metrics, instruments (see §4).
5. **Results** — SUS score, efficiency, inter-annotator agreement.
6. **Discussion** — implications, limitations (rule-based, small N, synthetic/CC data).
7. **Conclusion & Future Work** — real LLM backend, more modalities, larger study.
8. **Availability** — GitHub link, MIT license, live demo.

## 4. Evaluation design / 评估实验设计（论文的"硬通货"）

**Participants 受试者:** 15–20 high-school/undergrad students (convenience sample).
Minors require parental/guardian consent; participation anonymous & voluntary.

**Materials 材料:** 10 openly-licensed images (CC0 ultrasound + CC dental), so **no
patient data** is used.

**Procedure 流程:** short tutorial → each participant annotates the 10 images
(boxes + polygons, pick class) → exports COCO/YOLO → fills questionnaire.

**Metrics 指标:**
- *Efficiency*: mean time per image, annotations per minute.
- *Inter-annotator agreement*: mean pairwise **IoU** for boxes; label agreement
  (% / Fleiss' κ) for classes.
- *Usability*: **System Usability Scale (SUS)**, 10 items, 0–100 score.
- *(Optional, ties in AI Doctor)*: pre/post 5-question health-literacy quiz.

**Analysis 分析:** descriptive stats; paired t-test / Wilcoxon for pre vs post.
Report SUS mean ± SD (a score ≥ 68 is "above average").

**Threats to validity 局限:** small N, convenience sample, CC/synthetic (not clinical)
images, rule-based (not ML) triage — state these honestly.

## 5. Target venues / 目标会议（按门槛）

| Venue | Type | Notes / 截止时间（请核实当年） |
| --- | --- | --- |
| **Journal of Emerging Investigators (JEI)** | HS peer-reviewed journal | Rolling submission — easiest entry |
| **JSHS** (Junior Science & Humanities Symposium) | HS regional→national | Regional deadlines usually fall/winter |
| **Regeneron ISEF / affiliated fairs** | Science fair w/ proceedings | Local fair first; spring season |
| **IEEE MIT URTC** | Undergrad research conf | Abstract usually ~Aug, event Oct |
| Workshop/poster (e.g. AMIA student, CHI LBW) | Conf side-track | Higher bar; later option |

> Recommended first target: **JEI** (rolling, peer-reviewed, made for high-schoolers)
> and a **JSHS** regional submission. 推荐先投 JEI + JSHS。

## 6. Suggested timeline / 时间线（约 8–10 周）

1. Wk 1–2: finalize tool, write Intro + Related Work + System Design.
2. Wk 3–4: get consent, run pilot (2–3 people), fix issues.
3. Wk 5–6: run full study (15–20), collect data.
4. Wk 7: analysis + Results + figures.
5. Wk 8: Discussion/Conclusion, polish, internal review.
6. Wk 9–10: format for target venue, submit.

## 7. Honest caveat / 诚实提醒

A rule-based demo will not pass a top-tier ML venue. With a real usability study and
honest framing, it is a **legitimate, defensible student tools paper** — strong for
JEI / JSHS / science fairs and great for college applications. Don't overclaim
"diagnosis" or "AI accuracy"; claim **usability, openness, and educational value**.

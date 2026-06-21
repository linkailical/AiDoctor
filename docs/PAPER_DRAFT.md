# An Offline, Zero-Install Web Toolkit for Medical-Image Annotation and Health-Literacy Education: Design and Usability Evaluation

*Working first draft. Bracketed [ ] items are placeholders to fill after the study. 论文初稿，方括号处为实验后补填。*

**Author:** Linkaili, Portola High School
**Keywords:** medical image annotation, COCO, YOLO, symptom checker, health literacy, web tools, privacy

---

## Abstract

Annotating medical images and teaching basic health literacy usually rely on
installed software or cloud services that raise setup, cost, and privacy barriers —
especially for students and low-resource settings. We present an open-source,
**fully client-side** web toolkit with three components: (1) a browser-based image
**annotation tool** supporting bounding boxes and polygons with zoom/pan and export to
the standard **COCO** and **YOLO** formats; (2) **AI Doctor**, a bilingual (English/中文),
offline, rule-based **symptom-checker** demo that triages common symptoms with explicit
safety disclaimers; and (3) an **extensible, openly-licensed dental image dataset module**.
Because all processing happens in the browser, no image ever leaves the user's device.
We evaluate usability with [N] students using the System Usability Scale (SUS),
annotation efficiency, and inter-annotator agreement. Participants achieved a mean SUS of
[score] and produced annotations with a mean pairwise IoU of [value]. The toolkit is
released under the MIT license at [repo URL]. Results suggest that lightweight,
privacy-preserving web tools can make medical-image annotation and health education more
accessible.

## 1. Introduction

Machine learning for medical imaging depends on labeled data, but annotation tools are
often heavyweight desktop applications or cloud platforms that require installation,
accounts, or uploading sensitive images. For students learning about medical AI, these
barriers are significant. Separately, public-facing "symptom checkers" can support health
literacy but often hide their logic and overstate certainty.

We ask: *can a single, zero-install, privacy-preserving web page provide useful
medical-image annotation and health-literacy education?* We contribute:

1. A **client-only annotation tool** (boxes + polygons, zoom/pan) that exports standard
   **COCO** and **YOLO** labels, so annotations integrate directly into real ML pipelines.
2. **AI Doctor**, a **bilingual, offline, rule-based** triage demo with transparent logic
   and clear "not medical advice" disclaimers.
3. An **extensible, openly-licensed dataset module** (starter dental set) demonstrating how
   the tool supports dataset curation.
4. A **usability evaluation** with students.

## 2. Related Work

**Annotation tools.** Desktop and web tools such as LabelImg, CVAT, and Label Studio are
powerful but typically require installation or a server, and many send data to a backend.
Our tool is intentionally minimal and runs entirely in the browser.

**Symptom checkers.** Online symptom checkers vary in transparency and accuracy. We do not
claim diagnostic performance; AI Doctor is a transparent, rule-based teaching demo.

**Educational medical-AI tools.** Prior work shows hands-on tools improve engagement with
AI concepts. We target accessibility (offline, zero-install, bilingual) for students.

## 3. System Design

**Architecture.** The toolkit is a static single-page application (HTML/CSS/vanilla
JavaScript) with no backend. It can be opened from a local file or served as static
hosting (e.g., GitHub Pages). All computation — image rendering, annotation, export — runs
in the browser, so images never leave the device.

**Annotation tool.** Users load an image (or a built-in CC0 sample), then draw bounding
boxes or organ-boundary polygons and assign a class. A view transform supports
mouse-wheel zoom and pan; annotation coordinates are stored in original image pixels so
exports are resolution-independent. Export targets:
- **COCO**: `images`, `categories`, and `annotations` with `bbox`, `area`
  (polygon area via the shoelace formula), and `segmentation`.
- **YOLO**: per-image normalized `class cx cy w h` plus `classes.txt`.

**AI Doctor.** A data-driven knowledge base maps each symptom to follow-up questions
(severity, duration), warning signs (red flags), common causes, and self-care. Triage is a
transparent rule: any emergency red flag → emergency; any red flag or severe → urgent;
long duration or moderate → routine; otherwise self-care. All strings are bilingual.

**Dataset module.** A manifest (`dataset.js`) lists images by class with source, author,
and license; the gallery renders directly from it, so contributors extend the dataset by
editing one file.

**Design goals.** Offline, zero-install, privacy-preserving, bilingual, extensible, and
honest about limitations.

## 4. Evaluation Methods

**Participants.** [N=15–20] high-school/undergraduate students (convenience sample);
minors with guardian consent; voluntary and anonymous.

**Materials.** [10] openly-licensed images (CC0 ultrasound, CC dental) — no patient data.

**Procedure.** Brief tutorial → each participant annotates the image set (boxes +
polygons, class labels) → exports COCO/YOLO → completes a questionnaire.

**Measures.**
- *Efficiency*: mean time per image; annotations per minute.
- *Inter-annotator agreement*: mean pairwise IoU (boxes); label agreement / Fleiss' κ.
- *Usability*: System Usability Scale (SUS, 10 items).
- *Optional*: pre/post 5-item health-literacy quiz (AI Doctor).

**Analysis.** Descriptive statistics; paired t-test / Wilcoxon for pre vs post.

## 5. Results

*(To be completed after the study.)*
- SUS: mean [score] ± [SD] (≥68 = above average).
- Efficiency: [time/image], [annotations/min].
- Agreement: mean pairwise IoU [value]; label κ [value].
- Health-literacy quiz: pre [m1] → post [m2], p = [p].

## 6. Discussion

Anticipated finding: students can learn the tool quickly and produce usable annotations,
supporting the value of lightweight, privacy-preserving web tools in education.
**Limitations:** small convenience sample; CC/synthetic (not clinical) images; rule-based
(not ML) triage; no comparison to a baseline tool. These constrain generalizability.

## 7. Conclusion & Future Work

We presented an offline, zero-install web toolkit for medical-image annotation and
health-literacy education, with a usability evaluation. Future work: a real LLM backend
for AI Doctor, more imaging modalities, a baseline-tool comparison, and a larger study.

## Availability

Open-source (MIT) at [repo URL: https://github.com/linkailical/AiDoctor]; live demo at
[demo URL]. Sample images are CC0/CC BY-SA with attribution in the app.

## Acknowledgments / Ethics

No patient data was used; all images are openly licensed. Participation was voluntary,
anonymous, and (for minors) with guardian consent.

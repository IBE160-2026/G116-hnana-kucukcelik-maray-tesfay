# Product Brief: AI Study Buddy — Turn Your Own Curriculum into Verified Study Material

## Executive Summary

AI Study Buddy is a web application that turns a student's own lecture notes, slides and curriculum into summaries, flashcards and quizzes. Every generated item is linked back to the document and page it came from, so the student can check it. The student uploads material for a course, chooses level of detail and language, and gets a structured set of study material that is saved per course and can be reviewed until the exam.

The problem is not a lack of material. It is that turning a semester of slides into something you can actually practise with takes hours. Most students therefore reread instead of testing themselves, even though self-testing is the more effective way to learn. Those who use general chatbots get fast answers, but they cannot verify where the answers come from, and nothing is organised or kept for later.

The timing matters. Language models can now read long documents and produce reliable summaries and questions at low cost, and students already use AI in their studies. What is missing is a tool that makes that use grounded, verifiable and structured around how studying actually works.

## The Problem

A typical course leaves a student with hundreds of slides, several PDFs and their own notes. Before an exam they need to know what matters, practise recalling it, and find out what they have not understood.

Today they do one of three things. They **reread** slides and notes, which feels productive but gives weak retention. They **make flashcards and practice questions by hand** in tools like Anki or Quizlet, which works but takes so long that few keep it up for a whole course. Or they **paste text into a general chatbot**, which is fast but has real weaknesses. The answers may include content that is not in the curriculum, there is no way to see which page a claim is based on, long documents must be split up manually, and everything disappears into a chat history instead of being kept per course.

The cost is time spent producing study material instead of studying, false confidence from summaries nobody has checked, and cramming in the last week because there is no simple way to practise along the way.

## The Solution

A student logs in, creates a course (for example IBE160), and uploads lecture slides, notes or curriculum as PDF or text. For each document they choose level of detail and output language (Norwegian or English).

The application then gives them:

- **Summaries** at the chosen level of detail, organised by document and section.
- **Key concepts** with short definitions.
- **Flashcards** that the student reviews and marks as "knew it" or "didn't know it". Cards they miss come back more often.
- **Quizzes** with multiple choice and short-answer questions, an answer key, explanations, and AI feedback on written answers. Wrong answers are collected so the student can go back to their weak points.

Every summary point, flashcard and question shows its **source reference** (document and page), so the student can open the original and check it. All material is saved privately per user and per course, and can be edited, deleted or regenerated. What changes for the student is simple: they go from "I have 300 slides" to "I am practising on the things I don't know yet" in a few minutes, and they can trust what they are practising on.

## What Makes This Different

| Alternative today | Why students tolerate it | Why this approach is better |
|---|---|---|
| Rereading slides and notes | No setup, feels familiar | Active practice (quiz, flashcards) instead of passive reading |
| General chatbots (ChatGPT etc.) | Free, fast, already in use | Grounded in the student's own material, with page references, saved and organised per course |
| Anki / Quizlet | Proven for memorisation | Cards and questions are generated from the curriculum instead of typed by hand |
| Source-grounded AI notebooks (e.g. NotebookLM) | Good summaries with citations | Built around a complete study flow: course → material → practice → review of weak points |

The honest assessment: there is no technical moat here. Similar tools exist and can be built by others. The value is execution — a tight, focused study workflow where the output is verifiable, with good support for Norwegian-language material.

## Who This Serves

**Primary user:** a university or college student preparing for exams in a course with a large volume of slide- and PDF-based curriculum, who wants to practise actively but does not have time to make study material by hand.

What they are trying to do: understand the key points, test themselves, and know what they need to work more on. Success for them is starting to practise within minutes of uploading, trusting the content because they can check the source, and seeing that the number of wrong answers goes down over time.

**Secondary users:** students with Norwegian-language curriculum, who are poorly served by many English-first tools, and students who want to prepare study material together (later version).

## Success Criteria

| Signal | Metric / evidence | Target | When measured |
|---|---|---|---|
| User outcome | Time from upload of a 30-page PDF to first quiz ready | Under 2 minutes | Testing before delivery |
| Quality / trust | Share of generated questions that are correct and answerable from the source (manual review of 50 questions) | 90 % or more | Testing before delivery |
| Quality / trust | Share of source references that point to the correct page | 95 % or more | Testing before delivery |
| Adoption / behaviour | Fellow students in a user test (n = 5) who say they would use it for exam preparation | At least 4 of 5 | User test in the final project week |
| Security | A user can never see another user's material; API keys are never exposed to the browser | 0 failures in tests | Automated tests |
| Project delivery | All v1 capabilities demonstrated end to end | 100 % | Final delivery |

## Scope

**In for v1.**

1. Registration and login, with each user's material stored privately.
2. Course creation and upload of text-based PDFs and text files.
3. Generation of summaries (three detail levels), key concepts, flashcards and quizzes (multiple choice and short answer), in Norwegian or English.
4. Source reference (document + page) on every generated item.
5. Quiz mode with scoring, AI feedback on written answers and a list of weak points; flashcard review where missed cards are repeated more often.
6. Editing, deleting and regenerating generated material.

**Explicitly out of v1.**

1. Scanned PDFs (OCR) and interpretation of images and figures — tables are handled as extracted text only.
2. Sharing and collaboration between students.
3. Advanced spaced-repetition algorithms and a study plan toward an exam date.
4. Integration with Canvas or other learning platforms.
5. Native mobile app, payment, audio/video lectures and local language models.

These are deferred, not rejected. Several are natural next steps after v1.

## Open Decisions

These decision points from the project description will be settled in the PRD and architecture:

- **Choice of LLM and confidence:** which model gives the best balance of quality, cost and Norwegian-language support, and whether uncertain items should be flagged to the user.
- **Summary granularity:** per document, per section or per page.
- **Tables and figures:** text extraction only in v1; better handling later.
- **Local vs. cloud processing:** v1 uses a cloud API. Users must be clearly told that uploaded material is sent to an external provider.

## Vision

**Now (v1):** prove that students can go from their own curriculum to verified practice material in minutes, and that they trust and use it.

**Next:** a proper spaced-repetition algorithm, a study plan counting down to the exam date, support for scanned documents, and shared course decks between students in the same course.

**In 2–3 years:** a personal study coach that follows the student across courses, knows which topics they struggle with, and suggests what to practise today. With a lecturer mode, a teacher could upload the curriculum once and see anonymised, aggregated overviews of which topics the class finds hardest — giving feedback to the teaching, not just to the student.

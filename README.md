# Readaloud

<a href="https://doi.org/10.5281/zenodo.23954427"><img alt="DOI" src="https://zenodo.org/badge/DOI/10.5281/zenodo.23954427.svg"></a>
  
Readaloud reads Word (.docx) and LaTeX (.tex) documents aloud in the browser, one sentence at a time. It works in English and Korean. The interface comes in both languages, and in a document that mixes the two, each sentence is read with a voice for its own language. No document is included; you open your own.

[한국어 안내는 아래에 있습니다.](#한국어)

## Use

1. Open `index.html` in a browser. With GitHub Pages turned on, open `https://<username>.github.io/readaloud/`.
2. Drop a .docx or .tex file on the page, or choose one with **Open file**.
3. Press **Play**, or click any sentence to start from there.

- **Moving around:** the table of contents jumps between sections. Space plays or pauses, and ← → move by sentence.
- **Settings:**
  - Reading language: Auto (per sentence), Korean, or English.
  - Korean voice and English voice. A voice list appears only for a language the document contains.
  - Speed from 0.6× to 2×.
  - Whether to read captions, table cells, and notes.
  - Whether to skip cross-references such as "(Section 5.4)", "(표 3)", and "[12]".
- **Interface language:** follows the browser language (Korean if the browser is set to Korean, English otherwise). Switch it with the button at the top right.
- **Saved in this browser only:** your last document and position. The start screen offers **Resume** and **Clear**; the last document is never opened automatically.

## How documents are read

- **Language:**
  - In Auto, each sentence is checked for Hangul and Latin letters. Sentences that are mostly Hangul are read as Korean, the rest as English.
  - Numbers and very short labels take the language of the sentence before them.
  - Choosing Korean or English reads the whole document in that language.
- **Numbers and symbols** are read in the sentence's language:
  - "1958–2023" becomes "1958 to 2023" or "1958에서 2023".
  - θ becomes "theta" or "세타".
  - ≥ becomes "at least" or "이상".
- **docx:**
  - Heading 1–3 styles become the table of contents.
  - Tables are shown on the page and read row by row when Table cells is on.
  - Footnotes and endnotes are gathered under Notes at the end.
  - Images and equation objects are skipped.
  - Old .doc files cannot be read; save them as .docx first.
- **tex:**
  - `\section`, `\subsection`, and `\subsubsection` become the table of contents, and the `abstract` environment becomes "Abstract".
  - Equation environments (`equation`, `align`, and others) and `\[ \]` are skipped.
  - Inline math such as `$\theta$` is turned into symbols and read aloud.
  - Figure and table environments keep only their `\caption`.
  - `\cite`, `\ref`, and `\label` are removed, and `\footnote` text moves to Notes.
  - Files pulled in with `\input` or `\include` are not followed. Open a single merged .tex file.
- **Long sentences** are spoken in comma-separated pieces, because Chrome cuts off utterances longer than about 14 seconds.

## What is in the folder

- `index.html`: the whole page (interface, document conversion, and reading). No server, build step, or API key is needed.
- `vendor/mammoth.browser.min.js`: mammoth 1.13.0, which converts .docx in the browser. BSD-2-Clause; the full license is in `vendor/mammoth-LICENSE.txt`.
- **Speech:** the browser's Web Speech API (`speechSynthesis`), so the voices are the ones installed on the device and browser.
  - Desktop Edge offers the widest choice of natural-sounding voices.
  - Edge on Android gives web pages no voices.
- **Fonts:** Noto Serif KR and IBM Plex Sans KR from Google Fonts, both under the SIL Open Font License 1.1. Without an internet connection the page uses the device's own fonts.
- **Privacy:** an opened file is processed inside the browser and is not sent anywhere.

---

## 한국어

Readaloud는 Word(.docx)와 LaTeX(.tex) 문서를 브라우저에서 한 문장씩 소리 내어 읽어 주는 페이지입니다.
- 한국어와 영어를 모두 지원합니다. 화면 문구가 두 언어로 나오고, 두 언어가 섞인 문서는 문장마다 그 언어의 음성으로 읽습니다.
- 기본으로 들어 있는 문서는 없고, 읽을 파일은 직접 엽니다.

### 쓰는 법

1. `index.html`을 브라우저로 엽니다. GitHub Pages를 켰다면 `https://<사용자명>.github.io/readaloud/`로 엽니다.
2. 파일을 끌어다 놓거나 **파일 열기**로 .docx나 .tex를 고릅니다.
3. **재생**을 누르거나 아무 문장이나 누르면 그 문장부터 읽습니다.

- **이동:** 목차로 절을 건너뜁니다. 스페이스는 재생·정지, ←·→는 이전·다음 문장입니다.
- **설정:**
  - 읽기 언어: 자동(문장별), 한국어, 영어
  - 한국어 음성과 영어 음성. 문서에 있는 언어의 음성 목록만 나옵니다.
  - 속도: 0.6–2배
  - 표·그림 제목, 표 내용, 주를 읽을지
  - "(5.4절)", "(Section 5.4)", "[12]" 같은 괄호 속 참조를 건너뛸지
- **화면 언어:** 브라우저 언어가 한국어면 한국어, 그 밖이면 영어로 나옵니다. 오른쪽 위 버튼으로 바꿉니다.
- **저장:** 마지막 문서와 위치는 이 브라우저에만 남습니다.
  - 시작 화면에서 **이어 듣기**나 **기록 지우기**를 고를 수 있습니다.
  - 지난 문서를 자동으로 열지는 않습니다.

### 읽는 방식

- **언어:**
  - 자동이면 문장마다 한글과 로마자의 비율을 봅니다. 한글이 많으면 한국어, 아니면 영어로 읽습니다.
  - 숫자나 아주 짧은 문구는 앞 문장의 언어를 따릅니다.
  - 한국어나 영어를 고르면 문서 전체를 그 언어로 읽습니다.
- **숫자와 기호**는 그 문장의 언어로 읽습니다.
  - "1958–2023"은 "1958에서 2023" 또는 "1958 to 2023"이 됩니다.
  - θ는 "세타" 또는 "theta"가 됩니다.
  - ≥는 "이상" 또는 "at least"가 됩니다.
- **docx:**
  - 제목 1–3 스타일을 목차로 씁니다.
  - 표는 화면에 보이고, 표 내용을 켜면 행 단위로 읽습니다.
  - 각주·미주는 문서 끝 "주"에 모입니다.
  - 그림과 수식 개체는 건너뜁니다.
  - 예전 .doc 형식은 .docx로 저장해서 여세요.
- **tex:**
  - `\section`, `\subsection`, `\subsubsection`을 목차로 쓰고, `abstract` 환경은 "Abstract"로 둡니다.
  - 수식 환경(`equation`, `align` 등)과 `\[ \]`는 건너뜁니다.
  - 본문 속 `$…$`는 기호로 바꿔 읽습니다.
  - 그림·표 환경은 `\caption`만 남깁니다.
  - `\cite`, `\ref`, `\label`은 지우고, `\footnote`는 "주"로 옮깁니다.
  - `\input`·`\include`로 불러오는 다른 파일은 포함되지 않으니, 한 파일로 합친 .tex를 여세요.
- **긴 문장**은 쉼표 단위로 나눠 읽습니다. Chrome이 약 14초가 넘는 발화를 끊는 문제 때문입니다.

### 구성과 라이선스

- `index.html`: 화면, 문서 변환, 낭독 기능 전부. 서버, 빌드 도구, API 키가 필요 없습니다.
- `vendor/mammoth.browser.min.js`: docx를 브라우저 안에서 변환하는 mammoth 1.13.0입니다. BSD-2-Clause이며, 라이선스 전문은 `vendor/mammoth-LICENSE.txt`에 있습니다.
- **음성:** 브라우저의 Web Speech API(`speechSynthesis`)라서, 기기와 브라우저에 설치된 음성을 씁니다.
  - 데스크톱 Edge에서 고품질(Natural) 음성이 가장 많이 나옵니다.
  - Android용 Edge는 음성 목록을 주지 않습니다.
- **글꼴:** Google Fonts의 Noto Serif KR과 IBM Plex Sans KR입니다. 둘 다 SIL Open Font License 1.1이고, 인터넷이 없으면 기기의 기본 글꼴로 보입니다.
- **개인정보:** 연 파일은 이 브라우저 안에서만 처리하고 어디로도 보내지 않습니다.

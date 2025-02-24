# Fuiz

Host live quizzes freeely

<img src="https://gitlab.com/fuiz/website/-/raw/main/static/favicon.svg?ref_type=heads" width="128" height="128" alt="Fuiz icon">

[![License](https://img.shields.io/gitlab/license/fuiz/website?style=for-the-badge)](https://gitlab.com/fuiz/website/-/raw/main/LICENSE)

## About

The alternative to Kahoot with enhanced collaboration and problem-solving. Fuiz is a privacy-focused, open-source learning platform hosting user-generated quizzes. Instead of competition and memorization, we are committed to providing an accessible classroom tool that encourages teamwork and discussions.

## Main Instance

Website is hosted at [fuiz.org](https://fuiz.org). We will keep providing this instance for free as long as we are able to.

## Funding

Fund us at [OpenCollective](https://opencollective.com/fuiz). Your funds are invaluable.

If you cannot donate, please share the word!

## Translations

Fuiz is under heavy development so strings often keep getting changed and added. Nonetheless, if yoou want to add your translations, feel free to do so by creating a merge request adding your translation similar to [en.json](https://gitlab.com/fuiz/website/-/blob/main/messages/en.json).

## Contribution

If you want to contribute a non-trivial amount please create an issue first so we can collaborate more efficiently. At the moment I treat this repo as if I'm the solo developer. So expect stuff to be slightly janky.

## [Limits](https://gitlab.com/fuiz/game/-/blob/main/config.toml)

```toml
[fuiz]
max_slides_count = 100
max_title_length = 100
max_player_count = 1000

[fuiz.multiple_choice]
min_title_length = 0
max_title_length = 100
min_introduce_question = 1
max_introduce_question = 30
min_time_limit = 5
max_time_limit = 240
max_answer_count = 8

[fuiz.corkboard]
id_length = 16
max_alt_length = 200

[fuiz.answer_text]
max_length = 100

[fuiz.bingo]
max_answer_count = 100
```

## Hosting Fuiz Locally

Create a directory for fuiz and cd into it then:

### Setup Image Backend (Corkboard)

```bash
git clone https://gitlab.com/fuiz/corkboard
cd corkboard/
cargo run
```

### Setup Backend Server (Hosted-Server)
Back to the parent directory

```bash
git clone https://gitlab.com/fuiz/hosted-server
cd hosted-server/
cargo run
```

### Setup Fuiz Frontend (Website)


```bash
git clone https://gitlab.com/fuiz/website
cd website/
npm install
```

Create  `.env.local` inside `website` (should be the current directory now) with:

```config
AUTH_SECRET={random string: bunx auth auth secret}
PUBLIC_DISPLAY_PLAY_URL="127.0.0.1:5173"
PUBLIC_PLAY_URL="http://127.0.0.1:5173"
PUBLIC_BACKEND_URL="http://127.0.0.1:8080"
PUBLIC_WS_URL="ws://127.0.0.1:8080"
PUBLIC_CORKBOARD_URL="http://127.0.0.1:5040"
```

Note: some of these ports can be different depending on your environment.

Start the project

```
bun run dev
```

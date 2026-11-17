# Self-hosted для TikTok та Instagram

Добірка з [основного списку](README.md) під роботу креатора або бренду в TikTok / Instagram Reels:
планування постів, автоматизація, посилання в біо, аналітика, переклад, зберігання відео.
Записи скопійовано з README без змін; під кожним — навіщо це в коротких відео.

Позначки, як в основному списку: `⚠` — залежить від стороннього сервісу поза твоїм контролем
(для соцмереж це нормально: публікація завжди йде через API TikTok / Meta).

## Типовий конвеєр

```
ідея / тренд ──► відео 9:16 ──► підпис + хештеги ──► черга публікацій ──► посилання в біо ──► аналітика
 RSSHub,         video-shotcraft  Ollama /            Postiz              LinkStack /         Umami /
 changedetection (поза списком)   LanguageTool                            Shlink              Plausible
                                  LibreTranslate      ◄── n8n / Activepieces / Automatisch зшивають кроки ──►
```

Відео 9:16 можна зібрати кодом через [video-shotcraft](https://github.com/Vincentwei1021/video-shotcraft)
(composition `AiflPromoVertical`, `npm run render:vertical`). Цього інструмента немає в основному
списку, бо це не мережевий сервіс.

--------------------

## Планування та публікація

- [Postiz](https://postiz.com) `⚠` - Schedule posts, track the performance of your content, and manage all your social media accounts in one place (alternative to Buffer, Hootsuite, Sprout Social). ([Source Code](https://github.com/gitroomhq/postiz-app)) `AGPL-3.0` `Docker`
  - Головний інструмент добірки: черга й календар постів для TikTok, Instagram, YouTube, X тощо. Акаунти підключаються через офіційні API.
- [Socioboard](https://github.com/Socioboard-developers/Socioboard-5.0) `⚠` - Social media management, analytics, and reporting platform supporting nine social media networks out-of-the-box. `GPL-3.0` `Nodejs`
  - Альтернатива Postiz зі звітами; перевір, чи підтримує потрібні тобі мережі.

## Автоматизація

- [Activepieces](https://www.activepieces.com) - No-code business automation tool like Zapier or Tray. For example, you can send a Slack notification for each new Trello card. ([Source Code](https://github.com/activepieces/activepieces)) `MIT` `Docker`
  - Сценарії без коду: «нове відео в папці → згенерувати підпис → поставити в чергу Postiz».
- [Automatisch](https://automatisch.io) - Business automation tool that lets you connect different services like Twitter, Slack, and more to automate your business processes (alternative to Zapier). ([Source Code](https://github.com/automatisch/automatisch)) `AGPL-3.0` `Docker`
  - Ще одна вільна альтернатива Zapier.
- [Huginn](https://github.com/huginn/huginn) - Build agents that monitor and act on your behalf. `MIT` `Ruby`
  - Агенти-спостерігачі: стежити за згадками, конкурентами, новинами ніші.
- [n8n](https://n8n.io/) - Free node based Workflow Automation Tool. Easily automate tasks across different services. ([Source Code](https://github.com/n8n-io/n8n)) `Apache-2.0/Commons-Clause` `Nodejs`
  - Найпопулярніший варіант для таких конвеєрів, але ліцензія не повністю вільна, тому в основному списку він на сторінці [Non-Free](non-free.md).

## Ідеї та тренди

- [RSSHub](https://docs.rsshub.app) - Easy to use, and extensible RSS feed aggregator capable of generating RSS feeds from pretty much everything ranging from social media to university departments. ([Demo](https://rsshub.app), [Source Code](https://github.com/DIYgod/RSSHub)) `MIT` `Nodejs/Docker`
  - RSS-стрічки з профілів і хештегів, щоб стежити за нішею та конкурентами в одному місці.
- [FreshRSS](https://freshrss.org/) - Self-hostable RSS feed aggregator. ([Demo](https://demo.freshrss.org/i/), [Source Code](https://github.com/FreshRSS/FreshRSS)) `AGPL-3.0` `PHP/Docker`
  - Читалка для стрічок із RSSHub.
- [changedetection.io](https://changedetection.io/) - Stay up-to-date with web-site content changes. ([Source Code](https://github.com/dgtlmoon/changedetection.io)) `Apache-2.0` `Python/Docker`
  - Сповіщення, коли змінюється сторінка: ціни конкурентів, лендінги, сторінки трендів.

## Тексти: підписи, переклад, ШІ

- [Ollama](https://ollama.com/) - Get up and running with Llama 3.3, DeepSeek-R1, Phi-4, Gemma 3, and other large language models. ([Source Code](https://github.com/ollama/ollama)) `MIT` `Docker/Python`
  - Локальна мовна модель для чернеток підписів, хуків і хештегів без платних API.
- [LocalAI](https://localai.io/) - Run your AI models locally and generate images and audio (alternative to OpenAI and Claude). ([Source Code](https://github.com/mudler/LocalAI), [Clients](https://localai.io/gallery.html)) `MIT` `Docker/K8S`
  - Те саме плюс генерація зображень і аудіо (озвучка, обкладинки).
- [Libre Translate](https://libretranslate.com/) - Machine Translation API. ([Source Code](https://github.com/LibreTranslate/LibreTranslate)) `AGPL-3.0` `Docker/Python`
  - Переклад підписів і субтитрів, щоб одне відео виходило кількома мовами.
- [LanguageTool](https://languagetool.org/) - Proofread more than 20 languages. It finds many errors that a simple spell checker cannot detect. ([Source Code](https://github.com/languagetool-org/languagetool), [Clients](https://languagetool.org/insights/post/product-windows-app/)) `LGPL-2.1` `Java/Docker`
  - Перевірка граматики підписів (є українська).

## Посилання в біо та короткі посилання

- [LinkStack](https://linkstack.org/) - Link all your social media platforms easily accessible on one page, customizable through an intuitive, easy to use user/admin interface (alternative to Linktree and Manylink). ([Demo](https://linksta.cc/), [Source Code](https://github.com/LinkStackOrg/LinkStack)) `AGPL-3.0` `PHP/Docker`
  - Свій Linktree з адмінкою: одне посилання в біо TikTok / Instagram.
- [LittleLink](https://littlelink.io/) - Simplistic approach for links in bio with 100+ branded buttons (alternative to Linktree). ([Demo](https://littlelink.io/), [Source Code](https://github.com/sethcottle/littlelink)) `MIT` `Javascript`
  - Найпростіший варіант: статична сторінка, хостинг безкоштовний.
- [Shlink](https://shlink.io) - URL shortener with REST API and command line interface. Includes official progressive web application and docker images. ([Source Code](https://github.com/shlinkio/shlink), [Clients](https://shlink.io/apps)) `MIT` `PHP/Docker`
  - Короткі посилання з окремою статистикою для кожного відео чи кампанії.
- [Kutt](https://kutt.to) - Modern URL shortener with support for custom domains and custom URLs. ([Demo](https://kutt.to), [Source Code](https://github.com/thedevs-network/kutt)) `MIT` `Nodejs/Docker`
  - Те саме на своєму домені.

## Аналітика

- [Umami](https://umami.is/) - Simple, fast, privacy-focused (alternative to Google Analytics). ([Demo](https://cloud.umami.is/share/LGazGOecbDtaIwDr), [Source Code](https://github.com/umami-software/umami)) `MIT` `Nodejs/Docker`
  - Скільки людей прийшло з TikTok / Instagram на сайт або сторінку з посиланнями і що вони там зробили.
- [Plausible Analytics](https://plausible.io/) - Simple, lightweight (< 1 KB) and privacy-friendly web analytics. ([Source Code](https://github.com/plausible/analytics/)) `AGPL-3.0` `Elixir`
  - Альтернатива Umami з UTM-звітами.

## Медіатека та обмін файлами

- [Immich](https://immich.app/) - Photo and video backup solution directly from your mobile phone (alternative to Google Photos). ([Demo](https://github.com/immich-app/immich#demo), [Source Code](https://github.com/immich-app/immich)) `AGPL-3.0` `Docker`
  - Автобекап зйомок з телефона: сирі кадри для Reels не губляться і шукаються за змістом.
- [Nextcloud](https://nextcloud.com/) - Access and share your files, calendars, contacts, mail and more from any device, on your terms. ([Demo](https://try.nextcloud.com/), [Source Code](https://github.com/nextcloud/server), [Clients](https://apps.nextcloud.com)) `AGPL-3.0` `PHP/deb`
  - Спільна папка з монтажером або клієнтом плюс календар контенту.
- [HandBrake Web](https://github.com/TheNickOfTime/handbrake-web) - Use one or more instances of HandBrake video transcoder on a headless device via a web interface. `AGPL-3.0` `Docker`
  - Пакетне перекодування відео під вимоги платформ (H.264, розмір файлу).
- [Pingvin Share X](https://github.com/smp46/pingvin-share-x) - File sharing platform with support for logins, reverse shares, share expiry, S3 Buckets, advanced authentication, ClamAV for security scans and more (fork of Pingvin Share). `BSD-2-Clause` `Docker/Nodejs`
  - Передати великий відеофайл клієнту чи монтажеру за посиланням з терміном дії.

## Дизайн і планування контенту

- [penpot](https://penpot.app/) - Web-based design and prototyping platform meant for cross-domain teams. ([Source Code](https://github.com/penpot/penpot)) `MPL-2.0` `Docker`
  - Обкладинки Reels, каруселі, шаблони сторіз (вільна альтернатива Figma).
- [AppFlowy](https://appflowy.io/) - Build detailed lists of to-do’s for different projects while tracking the status of each one (alternative to Notion). ([Source Code](https://github.com/AppFlowy-IO/appflowy)) `AGPL-3.0` `Rust/Dart/Docker`
  - Контент-план: ідеї → сценарій → зйомка → монтаж → опубліковано.
- [Kanboard](https://kanboard.org/) - Simple visual task board. ([Source Code](https://github.com/kanboard/kanboard)) `MIT` `PHP`
  - Простіша канбан-дошка для того самого.

## З чого почати

1. **Мінімум:** LinkStack (біо) + Umami (аналітика). Обидва працюють на найдешевшому VPS через Docker.
2. **Регулярний постинг:** додай Postiz і підключи TikTok та Instagram (потрібен бізнес-акаунт або акаунт автора в Instagram).
3. **Автоматизація:** Activepieces або n8n зшивають рендер відео, підпис з Ollama і чергу в Postiz.

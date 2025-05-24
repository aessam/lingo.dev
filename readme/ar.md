<p align="center">
  <a href="https://lingo.dev">
    <img src="https://raw.githubusercontent.com/lingodotdev/lingo.dev/main/content/banner.dark.png" width="100%" alt="Lingo.dev" />
  </a>
</p>

<p align="center">
  <strong>⚡️ أداة سطر أوامر مفتوحة المصدر مدعومة بالذكاء الاصطناعي لترجمة وتعريب تطبيقات الويب والموبايل.</strong>
</p>

<br />

<p align="center">
  <a href="https://docs.lingo.dev">الدوكس</a> •
  <a href="https://github.com/lingodotdev/lingo.dev/issues?q=is%3Aissue+is%3Aopen+label%3A%22good+first+issue%22">المشاركة</a> •
  <a href="#-أكشن-github">أكشن GitHub</a> •
  <a href="#">حط نجمة للمشروع</a>
</p>

<p align="center">
  <a href="https://github.com/lingodotdev/lingo.dev/actions/workflows/release.yml">
    <img src="https://github.com/lingodotdev/lingo.dev/actions/workflows/release.yml/badge.svg" alt="الإصدار" />
  </a>
  <a href="https://github.com/lingodotdev/lingo.dev/blob/main/LICENSE.md">
    <img src="https://img.shields.io/github/license/lingodotdev/lingo.dev" alt="الرخصة" />
  </a>
  <a href="https://github.com/lingodotdev/lingo.dev/commits/main">
    <img src="https://img.shields.io/github/last-commit/lingodotdev/lingo.dev" alt="آخر كوميت" />
  </a>
</p>

<br />

Lingo.dev هي أداة سطر أوامر مفتوحة المصدر من المجتمع وبتشتغل بالذكاء الاصطناعي علشان تعرب وتترجم تطبيقات الويب والموبايل.

Lingo.dev مصممة عشان تعمل ترجمات حقيقية وطبيعية بسرعة، وده بيلغي الشغل اليدوي والتعقيدات الإدارية. النتيجة إن الفرق بتقدر تعمل تعريب دقيق أسرع 100 مرة، وتطلق ميزات لمستخدمين أكتر في كل حتة في العالم. ممكن تستخدمها مع نموذج اللغة الكبير بتاعك أو مع محرك الترجمة المُدار من Lingo.dev.

> **حاجة مش كتير يعرفوها:** Lingo.dev ابتدت كمشروع صغير في هاكاثون طلابي سنة 2023! وبعد كذا تطوير، اتقبلنا في Y Combinator سنة 2024، واحنا دلوقتي بنوظف! مهتم تشتغل معانا وتبني أدوات الترجمة للجيل الجاي؟ ابعت السيرة الذاتية بتاعتك على careers@lingo.dev! 🚀

## 📑 في الدليل ده

- [البداية السريعة](#-البداية-السريعة) - ابدأ في دقايق
- [التخزين المؤقت](#-التخزين-المؤقت-باستخدام-i18nlock) - تحسين تحديثات الترجمة
- [أكشن GitHub](#-أكشن-github) - أوتوماتيك للترجمة في CI/CD
- [المميزات القوية](#-المميزات-القوية) - اللي بيخلي Lingo.dev قوية
- [الدوكس](#-الدوكس) - أدلة وتفاصيل كاملة
- [المشاركة](#-المشاركة) - انضم لمجتمعنا

## 💫 البداية السريعة

أداة سطر الأوامر Lingo.dev متصممة عشان تشتغل مع نموذج اللغة الكبير بتاعك أو محرك الترجمة المُدار من Lingo.dev اللي مبني على أحدث نماذج اللغة الكبيرة (SOTA).

### استخدام نموذج اللغة الكبير بتاعك (BYOK أو أحضر مفتاحك الخاص)

1. اعمل ملف كونفيج `i18n.json`:

```json
{
  "version": 1.5,
  "provider": {
    "id": "anthropic",
    "model": "claude-3-7-sonnet-latest",
    "prompt": "You're translating text from {source} to {target}."
  },
  "locale": {
    "source": "en",
    "targets": ["es", "fr", "de"]
  }
}
```

2. حط مفتاح API بتاعك كمتغير بيئي:

```bash
export ANTHROPIC_API_KEY=your_anthropic_api_key

# أو لـ OpenAI

export OPENAI_API_KEY=your_openai_api_key
```

3. شغل الترجمة:

```bash
npx lingo.dev@latest i18n
```

### استخدام Lingo.dev Cloud

غالباً التطبيقات الإنتاجية بتحتاج ميزات زي ذاكرة الترجمة ودعم المصطلحات وتأكيد جودة الترجمة. كمان، ساعات هتحتاج حد خبير يختارلك أحسن مزود ونموذج LLM تستخدمه، ويحدثه تلقائي لما تظهر نماذج جديدة. Lingo.dev هو محرك ترجمة مُدار بيوفر الميزات دي كلها:

1. اعمل ملف كونفيج `i18n.json` (من غير نود المزود):

```json
{
  "version": 1.5,
  "locale": {
    "source": "en",
    "targets": ["es", "fr", "de"]
  }
}
```

2. سجل دخولك مع Lingo.dev:

```bash
npx lingo.dev@latest auth --login
```

3. شغل الترجمة:

```bash
npx lingo.dev@latest i18n
```

## 📖 الدوكس

علشان تلاقي شرح مفصل ومراجع الـ API، زور [الدوكس](https://lingo.dev/go/docs).

## 🔒 التخزين المؤقت باستخدام `i18n.lock`

Lingo.dev بيستخدم ملف `i18n.lock` عشان يتتبع الهاش (checksums) للمحتوى، وده بيضمن إن المحتوى المتغير بس هو اللي بيتترجم. ده بيحسن:

- ⚡️ **السرعة**: بيتخطى المحتوى اللي اتترجم قبل كده
- 🔄 **الثبات**: بيمنع إعادة الترجمة من غير ضرورة
- 💰 **التكلفة**: مفيش فواتير على الترجمات المتكررة

## 🤖 أكشن GitHub

Lingo.dev بيقدم أكشن GitHub علشان تأتمتة الترجمة في بايبلاين CI/CD بتاعك. خد بالك من الإعداد الأساسي ده:

```yaml
- uses: lingodotdev/lingo.dev@main
  with:
    api-key: ${{ secrets.LINGODOTDEV_API_KEY }}
```

الأكشن ده بيشغل `lingo.dev i18n` مع كل بوش، وده بيخلي الترجمات بتاعتك محدثة تلقائي.

علشان تعرف أكتر عن طريقة شغل البول ريكويست وإعدادات الكونفيج التانية، زور [دوكس الـ GitHub Action بتاعنا](https://docs.lingo.dev/ci-action/gha).

## ⚡️ المميزات القوية

- 🔥 **تكامل سريع**: بيشتغل مع الكود بتاعك في دقايق
- 🔄 **أتمتة CI/CD**: جهزه ونساها
- 🌍 **وصول عالمي**: اطلق لمستخدمين في كل مكان
- 🧠 **مدعوم بالذكاء الاصطناعي**: بيستخدم أحدث نماذج اللغة للترجمات الطبيعية
- 📊 **متوافق مع كل الصيغ**: JSON وYAML وCSV وMarkdown وAndroid وiOS وغيرها كتير
- 🔍 **اختلافات نظيفة**: بيحافظ على هيكل الملفات بتاعتك زي ما هي
- ⚡️ **سريع جداً**: ترجمات في ثواني، مش أيام
- 🔄 **دايما محدث**: بيتحدث تلقائي لما يتغير المحتوى
- 🌟 **جودة زي البني آدمين**: ترجمات مش باينة إنها آلية
- 👨‍💻 **اتعمل بواسطة مطورين، للمطورين**: بنستخدمه احنا كمان كل يوم
- 📈 **بينمو معاك**: من مشروع جانبي لحاجة كبيرة للشركات

## 🤝 المشاركة

Lingo.dev بيعتمد على المجتمع، فاحنا بنرحب بكل المشاركات!

عندك فكرة لميزة جديدة؟ اعمل إشيو على GitHub!

عايز تشارك؟ اعمل بول ريكويست!

## 🌐 الملف التعريفي بلغات تانية

- [الإنجليزية](https://github.com/lingodotdev/lingo.dev)
- [الصينية](/readme/zh-Hans.md)
- [اليابانية](/readme/ja.md)
- [الكورية](/readme/ko.md)
- [الإسبانية](/readme/es.md)
- [الفرنسية](/readme/fr.md)
- [الروسية](/readme/ru.md)
- [الألمانية](/readme/de.md)
- [الإيطالية](/readme/it.md)
- [العربية](/readme/ar.md)
- [الهندية](/readme/hi.md)
- [البنغالية](/readme/bn.md)

مش شايف لغتك؟ كل اللي عليك إنك تضيف كود لغة جديد في ملف [`i18n.json`](./i18n.json) واعمل بول ريكويست!

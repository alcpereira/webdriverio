---
id: coverage
title: கவரேஜ்
---

WebdriverIO இன் பிரௌசர் ரன்னர் [` istanbul `](https://istanbul.js.org/)ஐப் பயன்படுத்தி கோடு கவரேஜ் அறிக்கையிடலை ஆதரிக்கிறது. The testrunner will automatically instrument your code and capture code coverage for you.

## செட்அப்

கோடு கவரேஜ் அறிக்கையிடலை இயக்க, WebdriverIO பிரௌசர் ரன்னர் கான்பிகரேஷன் மூலம் அதை இயக்கவும், எ.கா.:

```js title=wdio.conf.js
export const config = {
    // ...
    runner: ['browser', {
        preset: process.env.WDIO_PRESET,
        coverage: {
            enabled: true
        }
    }],
    // ...
}
```

அனைத்து [coverage options](/docs/runner#coverage-options)ஐப் பார்க்கவும், அதை எவ்வாறு சரியாகக் கட்டமைப்பது என்பதை அறிய.

## கோடை புறக்கணித்தல்

கவரேஜ் டிராக்கிங்கிலிருந்து வேண்டுமென்றே விலக்க விரும்பும் உங்கள் கோட்பேஸின் சில பிரிவுகள் இருக்கலாம், இதைச் செய்ய, பின்வரும் பாகுபடுத்தும் குறிப்புகளைப் பயன்படுத்தலாம்:

- `/* istanbul ignore if */`: அடுத்த if அறிக்கையைப் புறக்கணிக்கவும்.
- `/* istanbul ignore else */`: if அறிக்கையின் else பகுதியைப் புறக்கணிக்கவும்.
- `/* istanbul ignore next */`: source-codeஇல் next thingயை புறக்கணிக்கவும் ( functions, if statements, classes, you name it).
- `/* istanbul ignore file */`: முழு source-fileயை புறக்கணிக்கவும் (இது பைலின் மேல் பகுதியில் வைக்கப்பட வேண்டும்).

:::info

`execute` அல்லது `executeAsync` கட்டளைகளை அழைக்கும்போது பிழைகளை ஏற்படுத்தக்கூடும் என்பதால், உங்கள் டெஸ்ட் பைல்களை கவரேஜ் அறிக்கையிடலிலிருந்து விலக்கப் பரிந்துரைக்கப்படுகிறது. உங்கள் அறிக்கையில் அவற்றை வைத்திருக்க விரும்பினால், பின்வரும் வழிகளில் அவற்றைப் பயன்படுத்துவதைத் தவிர்க்கவும்:

```ts
await browser.execute(/* istanbul ignore next */() => {
    // ...
})
```

:::

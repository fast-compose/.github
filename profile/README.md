<div align="center">

<img src="https://raw.githubusercontent.com/fast-compose/fast-compose/main/docs/images/logo.png" width="180" alt="Fast Compose logo">

# [Fast Compose](https://github.com/fast-compose/fast-compose)

### An instant runtime for Jetpack Compose code. No compiler, no build, no waiting.

Write Compose code and watch it render in milliseconds, on Android, iOS, desktop and the web.

[**🌐 Website**](https://fast-compose.github.io) &nbsp;·&nbsp;
[**▶️ Playground**](https://fast-compose.github.io/playground/) &nbsp;·&nbsp;
[**📦 Engine**](https://github.com/fast-compose/fast-compose) &nbsp;·&nbsp;
[**🧩 Plugin**](https://plugins.jetbrains.com/plugin/35776-fast-compose-preview) &nbsp;·&nbsp;
[**📜 Compose Script**](https://github.com/fast-compose/compose-script) &nbsp;·&nbsp;
[**⌨️ CLI**](https://github.com/fast-compose/compose-cli)

[![Maven Central](https://img.shields.io/maven-central/v/io.github.fast-compose/fast-compose?label=Maven%20Central&color=6E56CF)](https://central.sonatype.com/namespace/io.github.fast-compose)
[![JetBrains Marketplace](https://img.shields.io/jetbrains/plugin/v/35776?label=Marketplace&logo=jetbrains&color=6E56CF)](https://plugins.jetbrains.com/plugin/35776-fast-compose-preview)
[![npm](https://img.shields.io/npm/v/@fast-compose/compose-script?label=npm&logo=npm&color=6E56CF)](https://www.npmjs.com/package/@fast-compose/compose-script)
![Kotlin Multiplatform](https://img.shields.io/badge/Kotlin-Multiplatform-7F52FF?logo=kotlin&logoColor=white)
[![License](https://img.shields.io/badge/license-Apache%202.0-blue.svg)](https://github.com/fast-compose/fast-compose/blob/main/LICENSE)

</div>

---

<div align="center">

# HISTORY AND PHILOSOPHY

</div>

🎆 Remember, Remember the Fifth of November! That was the day I introduced the **Fast Compose** project to the world.

The idea started with the very first line I wrote in Compose! No Instant Preview like XML. I had to build the entire
app just to see my changes. Every little UI modification made the preview outdated and required another rebuild.

JetBrains introduced a Hot Reload plugin. Sounds good, but that's not what Android and KMP developers deserve! They
deserve to write Compose and see their UI instantly, just like they do when writing HTML.

### 📅 October 28, 2026

The idea for this project started on October 28, 2026. I came across [DartPad](https://dartpad.dev/), and that made me
anxious. **I hate Flutter!** I see it everywhere in the browser world! Flutter previews are embedded right into the
[Flutter documentation](https://docs.flutter.dev/ui), where you can compile and see a preview in just a few seconds.

**But we, the great Compose developers, don't have that!**

Before November 5th, all we had was Kotlin Playground. It could run Compose code by compiling it on a server and
displaying the result as a preview. So slow, so primitive! That made me even more frustrated.

I opened Claude and asked how we could run Compose previews directly inside the browser. Could we port the Kotlin
Multiplatform plugin or the Hot Reload plugin to WASM?

The answers were disappointing. Compose relies heavily on the JVM and is stuck there! Even Compose Multiplatform
Preview in Android Studio (before November 5th) couldn't work without the Android target because it relies on
AndroidX tooling.

The proposed solution? Run the actual Kotlin compiler in the browser and build the app there!

Imagine downloading hundreds of megabytes and waiting several seconds just to build an app! That's absolutely what I
was trying to avoid.

### 💡 The game changer

Until Claude suggested what he called **"A real game changer": a Compose Interpreter!**

What the hell, man? Are we going to reinvent the wheel? Actually, we won't! But if you really want to do that and have enough tokens, you can give it a try.

We simply can't compile Compose code at runtime, but we can make the runtime call the Compose APIs directly to render
dynamic Compose UI within milliseconds.

If you haven't got the idea yet, check [**fast-compose/fast-compose**](https://github.com/fast-compose/fast-compose)!

So, why didn't Google or JetBrains build this interpreter?

I don't know. But I remembered this quote:

<div align="center">

> ***"Ideas lie scattered along the roadside; what distinguishes people is how they recognize, refine, and articulate them."***<br>
> — [Al-Jahiz](https://en.wikipedia.org/wiki/Al-Jahiz)

</div>

On October 28th, I recognized one of those ideas and started implementing it in pure Kotlin as a KMP project.

The results were amazing! I was so satisfied with Claude Code that I even rewarded it with a mention in the initial
commits as a co-author. I don't usually do that! 😂

<div align="center">

## ✨ Great ideas inspire even greater ideas.

</div>

I started thinking: We now have an instant Compose runtime, implemented entirely in Kotlin and supporting KMP. Why
stop there?

---

### <img src="https://raw.githubusercontent.com/fast-compose/playground/main/docs/images/logo.png" height="36" align="absmiddle" alt=""> Fast Compose Playground

The original vision was a web-first playground, designed to be a serious competitor to Kotlin Playground.

However, it eventually evolved into mobile and desktop applications too. Now Android developers can run Compose code
instantly on their devices. Pretty cool!

<div align="center">

<img src="https://raw.githubusercontent.com/fast-compose/playground/main/docs/images/showcase.png" width="100%" alt="Fast Compose Playground on Android, desktop and the web">

[**▶️ Open in the browser**](https://fast-compose.github.io/playground/) &nbsp;·&nbsp;
[**🤖 Google Play**](https://play.google.com/store/apps/details?id=ma7moud3ly.fast.compose.playground) &nbsp;·&nbsp;
[**🖥️ Windows, macOS, Linux**](https://github.com/fast-compose/playground/releases/latest) &nbsp;·&nbsp;
[**📂 Source**](https://github.com/fast-compose/playground)

</div>

### <img src="https://raw.githubusercontent.com/fast-compose/fast-compose/main/docs/images/logo.png" height="36" align="absmiddle" alt=""> Fast Compose Preview

The engine could also be exposed as a public library
[![Maven Central](https://img.shields.io/maven-central/v/io.github.fast-compose/fast-compose?label=Maven%20Central&color=6E56CF)](https://central.sonatype.com/artifact/io.github.fast-compose/fast-compose)

```kotlin
implementation("io.github.fast-compose:fast-compose:x.y.z")
```

As a KMP developer, you could simply include it in your project to evaluate dynamic Compose code or ship dynamic UI
features directly inside your app.

```kotlin
val code = rememberComposeCode("""
    @Preview
    @Composable
    fun Hello() {
        Text("Hello, Fast Compose!")
    }
""".trimIndent())

FastComposePreview(code)
```

📦 [**fast-compose/fast-compose**](https://github.com/fast-compose/fast-compose)

### <img src="https://raw.githubusercontent.com/fast-compose/compose-script/main/docs/images/logo.png" height="36" align="absmiddle" alt=""> Compose Script

Since the engine was already ported to WASM, we could build a small JavaScript bridge and use it to run Compose code
directly inside static HTML pages!

```html
<script src="https://cdn.jsdelivr.net/npm/@fast-compose/compose-script/compose-script.js"></script>

<script type="text/compose-content">
  var count by remember { mutableStateOf(0) }

  Button(onClick = { count++ }) {
    Text("Clicked $count times")
  }
</script>
```

That brilliant idea became **Compose Script**, something I'm really proud of.

> The [**Fast Compose website**](https://fast-compose.github.io) is made with Fast Compose: the whole page is one
> Compose app inside a single `<script type="text/compose-content">` tag.

Try it live on CodePen: [Sound Wave](https://codepen.io/editor/ma7moud3ly/pen/01a191f5-6523-799c-81ed-a193e00bf1f2) ·
[Travel Explorer](https://codepen.io/editor/ma7moud3ly/pen/01a1921f-0a2c-71e4-8e02-5a7de6fd32be) ·
[Live Showcase](https://codepen.io/editor/ma7moud3ly/pen/01a191d9-c6a9-782f-a17c-9df79dc2063b)

📦 [**fast-compose/compose-script**](https://github.com/fast-compose/compose-script)

### <img src="https://raw.githubusercontent.com/fast-compose/intellij-plugin/main/docs/images/logo.png" height="36" align="absmiddle" alt=""> Android Studio Plugin

And I didn't forget the motherland: **Android Studio!**

Building the **[Fast Compose Preview](https://plugins.jetbrains.com/plugin/35776-fast-compose-preview)** plugin was
probably the biggest challenge, especially when I started testing it against real projects.

It was fast and amazing, but I also realized that the Fast Compose engine still lacked a lot of functionality. That
pushed me to release **v0.2.0** and continue improving it.

> **Settings → Plugins → Marketplace**, search for **Fast Compose Preview**, then open a Kotlin file with `@Preview`
> functions.

📦 [**fast-compose/intellij-plugin**](https://github.com/fast-compose/intellij-plugin)

### <img src="https://raw.githubusercontent.com/fast-compose/compose-cli/main/docs/images/logo.png" height="36" align="absmiddle" alt=""> Fast Compose CLI

Finally, while surfing LinkedIn, I came across some enthusiastic developers discussing the Android CLI and how they use
it to render Compose UI directly from the command line.

**Heeeh, guys! Fast Compose can do it better and instantly!** 

📦 [**fast-compose/compose-cli**](https://github.com/fast-compose/compose-cli)

---

Yeah, that's how the Fast Compose project started.

> ***But you used Claude Code to implement it! Where is the human part?!***

I told you I hate Flutter! I don't like Kotlin Playground! I wanted to run Compose in the browser! I've struggled for
years with outdated Compose previews! These are my problems, my frustrations, and my experience!

Claude suggested the interpreter. Without Claude, there wouldn't have been an interpreter within a week! No doubt about
that.

- But I decided to build the playground, the KMP library, and the JetBrains plugin.
- I asked Claude if Compose Script was possible while we were supporting wasmJs. He said yes! I literally jumped out of my chair.
- I thought about a future WASM-based VS Code plugin. He agreed!
- I thought the CLI would be cool. He said, why not an MCP server for AI agents too?

I told him I love you man 😂

That's the beauty of it! I bring the ideas, the experience, and the direction. Claude helps me execute my dreams.

I'm really grateful for this idea. The results were incredibly motivating, and in just a few days, the project was
ready to meet the world.

<div align="center">

---

# 🎆 Remember, remember the Fifth of November!

<br>

[**Mahmoud Aly**](https://github.com/Ma7moud3ly)<br>
<sub>5 November 2026</sub>

<br>

*Built with ❤️ and Kotlin*

</div>

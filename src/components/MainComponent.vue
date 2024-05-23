<template>
  <div id="main">
    <div class="door-container">
      <div class="door-left"></div>
      <div class="door-right"></div>
    </div>
    <div class="section top-section">
      <div class="background-image">
        <img src="../assets/ottan.webp" alt="おったんの画像" class="background-image__image">
      </div>
      <div class="content">
        <h1 class="title">おったん部屋🎶〜終業後の癒し〜</h1>
        <p class="description">君のモンタは明日へのモンタッ🫵</p>
        <div class="button-container">
          <button class="custom-button" @click="closeDoorsAndScroll('intro')">紹介</button>
          <button class="custom-button" @click="closeDoorsAndScroll('game')">遊戯</button>
          <button class="custom-button" @click="closeDoorsAndScroll('blog')">雑記</button>
          <button class="custom-button" @click="closeDoorsAndScroll('qa')">質疑</button>
        </div>
      </div>
    </div>
    <div id="intro" class="section intro-section">
      <div class="background-image-intro">
        <img src="../assets/intro-background.webp" alt="紹介の背景画像" class="background-image__image-intro">
      </div>
      <div class="content">
        <h2>紹介</h2>
        <p>我が名はおったん🎶<br>実家を生業とし怠惰を極めし者！</p>
      </div>
    </div>
    <div id="game" class="section game-section">
      <div class="background-image-game">
        <img src="../assets/game-background.webp" alt="遊戯の背景画像" class="background-image__image-game">
      </div>
      <div class="content">
        <h2>遊戯</h2>
        <p><a class="twitter-timeline" href="https://twitter.com/kamekame5312?ref_src=twsrc%5Etfw">Tweets by kamekame5312</a> <script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script></p>
        <p>おったんのゲーム実況は<a href="https://www.twitch.tv/nanasin5555" target="_blank">こちら</a></p>
      </div>
    </div>
    <div id="blog" class="section blog-section">
      <div class="background-image-blog">
        <img src="../assets/blog-background.webp" alt="雑記の背景画像" class="background-image__image-blog">
      </div>
      <div class="content">
        <h2>雑記</h2>
        <p>ここは雑記用のページです。日々の出来事や考えたことをここに書きます。</p>
      </div>
    </div>
    <div id="qa" class="section qa-section">
      <div class="background-image-qa">
        <img src="../assets/qa-background.webp" alt="質疑の背景画像" class="background-image__image-qa">
      </div>
      <div class="content">
        <h2>質疑</h2>
        <p>ここは質疑用のページです。質問や疑問に答えます。</p>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'MainComponent',
  methods: {
    closeDoorsAndScroll(id) {
      const doorContainer = document.querySelector('.door-container');
      doorContainer.style.display = 'flex'; // 扉を再表示
      setTimeout(() => {
        doorContainer.classList.remove('open'); // 扉を閉じる
        setTimeout(() => {
          this.scrollToSection(id);
          setTimeout(() => {
            doorContainer.classList.add('open'); // 扉を再度開く
            setTimeout(() => {
              doorContainer.style.display = 'none'; // 扉を再度非表示
            }, 1500); // アニメーション終了後に扉を非表示にする
          }, 500); // ページが読み込まれてから0.5秒後に扉を開く
        }, 1500); // 扉を閉じるアニメーションが終了するのを待つ
      }, 0); // 直ちに扉を閉じるアニメーションを開始
    },
    scrollToSection(id) {
      const element = document.getElementById(id);
      if (element) {
        window.scrollTo({ top: element.offsetTop, behavior: 'smooth' });
      }
    }
  },
  mounted() {
    setTimeout(() => {
      document.querySelector('.door-container').classList.add('open');
      setTimeout(() => {
        document.querySelector('.door-container').style.display = 'none';
      }, 1500); // アニメーション終了後に扉を非表示にする
    }, 500); // ページが読み込まれてから0.5秒後に扉を開く
  }
}
</script>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Hannari&display=swap');

#main {
  font-family: 'Hannari', serif;
  max-width: 100%;
  margin: 0 auto;
  position: relative;
  overflow: hidden;
}

.section {
  height: 100vh;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  position: relative;
  overflow: hidden;
}

.top-section .content, .intro-section .content, .game-section .content, .blog-section .content, .qa-section .content {
  position: relative;
  z-index: 1;
  text-align: center;
  color: #333; /* コンテンツの色を設定 */
}

.background-image, .background-image-intro, .background-image-game, .background-image-blog, .background-image-qa {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  z-index: 0;
  opacity: 0.2;
  pointer-events: none; /* クリックイベントを無効化 */
}

.background-image__image, .background-image__image-intro, .background-image__image-game, .background-image__image-blog, .background-image__image-qa {
  width: 100%;
  height: 100%;
  object-fit: cover;
}

.title {
  font-family: 'Hannari', serif;
  font-size: 2.5em;
}

.description {
  font-size: 1.6em;
  margin-bottom: 20px;
  font-weight: bold;
}

.button-container {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  gap: 10px;
  justify-items: center;
  margin-top: 20px;
}

.custom-button {
  padding: 20px 80px;
  font-size: 2em;
  background-color: #e7cfb5;
  border: none;
  border-radius: 5px;
  cursor: pointer;
  transition: background-color 0.3s;
  font-family: Hannari, serif;
}

.custom-button:hover {
  background-color: #d1b495;
}

.intro-section h2, .game-section h2, .blog-section h2, .qa-section h2 {
  font-size: 2.5em;
  margin-bottom: 20px;
}

.intro-section p, .game-section p, .blog-section p, .qa-section p {
  font-size: 1.2em;
}

/* 扉のアニメーション */
.door-container {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  display: flex;
  z-index: 100; /* 最前面に表示 */
}

.door-left, .door-right {
  width: 50%;
  height: 100%;
  background: repeating-linear-gradient(
    30deg,
    #000, #000 3px,
    rgba(255, 255, 255, 0) 3px 28px,
    #000 28px 31px
  ),
  repeating-linear-gradient(
    -30deg,
    #000, #000 3px,
    rgba(255, 255, 255, 0) 3px 28px,
    #000 28px 31px
  ),
  repeating-linear-gradient(
    30deg,
    #fff, #fff 6px,
    rgba(255, 255, 255, 0) 6px 25px,
    #fff 25px 31px
  ),
  repeating-linear-gradient(
    -30deg,
    #fff, #fff 6px,
    rgba(255, 255, 255, 0) 6px 25px,
    #fff 25px 31px
  ),
  repeating-linear-gradient(
    30deg,
    #000, #000 7.5px,
    rgba(255, 255, 255, 0) 7.5px 23.5px,
    #000 23.5px 31px
  ),
  repeating-linear-gradient(
    -30deg,
    #000, #000 7.5px,
    rgba(255, 255, 255, 0) 7.5px 23.5px,
    #000 23.5px 31px
  ),
  repeating-linear-gradient(
    30deg,
    #fff, #fff 9px,
    rgba(255, 255, 255, 0) 9px 15px,
    #fff 15px 16px,
    rgba(255, 255, 255, 0) 16px 22px,
    #fff 22px 31px
  ),
  repeating-linear-gradient(
    -30deg,
    #fff, #fff 9px,
    rgba(255, 255, 255, 0) 9px 15px,
    #fff 15px 16px,
    rgba(255, 255, 255, 0) 16px 22px,
    #fff 22px 31px
  ),
  repeating-linear-gradient(
    30deg,
    #000, #000 15px,
    rgba(255, 255, 255, 0) 15px 16px,
    #000 16px 31px
  ),
  repeating-linear-gradient(
    -30deg,
    #000, #000 15px,
    rgba(255, 255, 255, 0) 15px 16px,
    #000 16px 31px
  );
  position: absolute;
  top: 0;
  transition: transform 1.5s ease-in-out;
}

.door-left {
  left: 0;
  transform: translateX(0);
}

.door-right {
  right: 0;
  transform: translateX(0);
}

.door-container.open .door-left {
  transform: translateX(-100%);
}

.door-container.open .door-right {
  transform: translateX(100%);
}
</style>

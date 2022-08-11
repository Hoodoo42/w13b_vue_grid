<template>
  <div id="tweet_container">
    <button id="toggle">Tweet Toggler</button>
  </div>
</template>

<script>
export default {
  methods: {
    toggleTweets() {
      let tweetContainer = document.getElementById(`tweet_container`);
      if (
        (tweetContainer[`style`][
          `grid-template-columns`
        ] = `repeat(auto-fit,minmax(250px,1fr));`)
      ) {
        (tweetContainer[`style`][`grid-template-columns`] = ""),
          (tweetContainer[`style`][`grid-template-rows`] = `auto`);
      } else {
        (tweetContainer[`style`][`grid-template-rows`] = ""),
          (tweetContainer[`style`][
            `grid-template-columns`
          ] = `repeat(auto-fit,minmax(250px,1fr));`);
      }
    },
  },

  showTweets() {
    for (let i = 0; i < this.tweets.length; i++) {
      let tweetContainer = document.getElementById(`tweet_container`);
      tweetContainer[`innerHTML`] =
        tweetContainer[`innerHTML`] +
        `<h2>${this.tweets[i][`user`]}</h2>` +
        `<h4>${this.tweets[i][`date`]}</h4>` +
        `<h3>${this.tweets[i][`tweet`]}</h3>`;
    }
  },

  data() {
    return {
      tweets: [
        {
          user: `River`,
          tweet: `Today I started my first attempt at a raft!`,
          date: `07/23/2020`,
        },
        {
          user: `Brook`,
          tweet: `One of my favourtie things about being a mom is hearing my baby babbling`,
          date: `11/23/2017`,
        },
        {
          user: `Willow`,
          tweet: `I sat under the big tree today and just read my book. It was so peacecul`,
          date: `06/14/2021`,
        },
      ],
    };
  },
  mounted() {

    this.showTweets();

    let toggle = document.getElementById(`toggle`);
    toggle.addEventListener(`click`, this.toggleTweets);

  },
};
</script>

<style scoped>
#tweet_container {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
  place-items: center;
  text-align: center;
}
</style>
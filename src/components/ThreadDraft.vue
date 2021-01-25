<template>
  <tweet-area
    @keydown="handleKeyDown($event)"
    @update:focus="setCurrentlyFocusedArea($event)"
    v-for="tweet in tweets"
    :key="tweets.indexOf(tweet)"
    :position="tweets.indexOf(tweet)"
    :ref="'tweetArea' + tweets.indexOf(tweet).toString()"
    v-model="tweet.text"
  />
  <strong>{{ fullText }}</strong>
</template>

<script>

import TweetArea from "./TweetArea.vue";

export default {
  components: {
    TweetArea,
  },

  data() {
    return {
      fullText: "",
      tweets: [{ text: "Write thread here." }],
    };
  },

  methods: {
    createEmptyTweet() {
      this.tweets.push({
        text: "",
      });
    },

    setCurrentlyFocusedArea(event) {
      this.currentlyFocusedArea = event
    },

    handleKeyDown(event) {
     
        if (event.shiftKey && event.key === "Enter") {
          if (!this.isLastTweetEmpty) {
            this.createEmptyTweet();
          }
          event.preventDefault();
          
        }
    },
  },

  computed: {
    isLastTweetEmpty() {
      return this.tweets[this.tweets.length - 1].text === "";
    },

    fullText() {
      const tweetTexts = this.tweets.map((tweet) => {
        return tweet.text;
      });
      return tweetTexts.join("\n");
    }
  },
};
</script>

<style></style>

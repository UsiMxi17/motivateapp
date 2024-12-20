<template>
  <div class="motivational-app">
    <h1>{{ title }}</h1>
    <p>{{ description }}</p>

    <div class="quote-section">
      <blockquote>"{{ currentQuote }}"</blockquote>
      <p>- {{ currentAuthor }}</p>
      <button @click="generateQuote">Get Inspired ✨</button>
    </div>

    <div class="quote-creation-section">
      <h2>Add Your Own Quote</h2>
      <input v-model="newQuote" placeholder="Enter your quote" />
      <input v-model="newAuthor" placeholder="Enter the author's name" />
      <button @click="addQuote">Add Quote</button>
    </div>

    <footer>
      <p>
        Powered by Vue.js |
        <a href="https://vuejs.org" target="_blank" rel="noopener"
          >Learn More</a
        >
      </p>
    </footer>
  </div>
</template>

<script>
export default {
  name: "MotivationalApp",
  data() {
    return {
      title: "Motivational Quotes App",
      description:
        "Click the button below to discover a new motivational quote and boost your day!",
      quotes: [
        // Initial Quotes
        {
          text: "The best way to predict the future is to create it.",
          author: "Peter Drucker",
        },
        {
          text: "Your time is limited, don’t waste it living someone else’s life.",
          author: "Steve Jobs",
        },
        {
          text: "If you are not willing to be a fool, you can’t become a master.",
          author: "Jordan Peterson",
        },
        {
          text: "You can tolerate doubt as a backseat driver, but if you put doubt in the pilot’s seat, defeat is guaranteed.",
          author: "David Goggins",
        },
        {
          text: "What lies behind you and what lies in front of you, pales in comparison to what lies inside of you.",
          author: "Ralph Waldo Emerson",
        },
        {
          text: "Whether you think you can or you think you can’t, you’re right.",
          author: "Henry Ford",
        },
        {
          text: "Success is not how high you have climbed, but how you make a positive difference.",
          author: "Roy T. Bennett",
        },
        {
          text: "Do what you can, with what you have, where you are.",
          author: "Theodore Roosevelt",
        },
      ],
      currentQuote: "",
      currentAuthor: "",
      newQuote: "",
      newAuthor: "",
    };
  },
  methods: {
    generateQuote() {
      const randomIndex = Math.floor(Math.random() * this.quotes.length);
      this.currentQuote = this.quotes[randomIndex].text;
      this.currentAuthor = this.quotes[randomIndex].author;
    },
    addQuote() {
      if (this.newQuote && this.newAuthor) {
        this.quotes.push({ text: this.newQuote, author: this.newAuthor });
        this.newQuote = "";
        this.newAuthor = "";
        alert("Quote added successfully!");
      } else {
        alert("Please enter both quote and author.");
      }
    },
  },
  mounted() {
    this.generateQuote();
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.motivational-app {
  font-family: "Arial", sans-serif;
  text-align: center;
  padding: 20px;
  background: linear-gradient(to bottom, #920eea, #e45daa);
  min-height: 100vh;
  color: #fff;
}

h1 {
  font-size: 2.5rem;
  margin-bottom: 10px;
}
p {
  font-size: 1.2rem;
  margin: 10px 0;
}

.quote-section {
  margin: 20px auto;
  padding: 20px;
  background: rgba(255, 255, 255, 0.2);
  border-radius: 10px;
  max-width: 600px;
}
blockquote {
  font-style: italic;
  font-size: 1.5rem;
  margin: 0 0 10px;
}
button {
  background-color: #ff6f61;
  border: none;
  color: #fff;
  padding: 10px 20px;
  font-size: 1rem;
  border-radius: 5px;
  cursor: pointer;
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
  position: relative; /* Added for floating effect */
  transition: background-color 0.3s, transform 0.3s; /* Smooth transition */
}
button:hover {
  background-color: #e65a50;
  transform: translateY(-5px); /* Float effect */
}

footer {
  margin-top: 30px;
  font-size: 0.9rem;
}
footer a {
  color: #fff;
  text-decoration: underline;
}
</style>

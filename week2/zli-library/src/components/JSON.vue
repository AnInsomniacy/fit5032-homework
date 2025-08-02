<!--
  JSON Data & Vue Directives Lab
  Author: zetao li
  Student ID: 34304525
-->
<template>
  <div class="json-lab">
    <h1>🗄️ JSON Data & Vue Directives Lab</h1>

    <section class="lab-section">
      <h2>📚 Working with JSON Arrays</h2>
      <p>Our <code>authors.json</code> contains an array of author objects.</p>

      <h3>Iterating through Arrays</h3>
      <!-- Activity 6: Render a list containing author names and their birth years. Hint: Make use of the v-for directive to iterate through the array of authors. -->
      <ul>
        <li v-for="author in authors" :key="author.id">
          {{ author.name }} ({{ author.birthYear }})
        </li>
      </ul>

      <h3>Filtering Arrays</h3>
      <!-- Activity 7: Render a list containing authors born after 1850. Hint: Make use of the v-for directive to iterate through the array of authors that you have filtered out. -->
      <p>Authors born after 1850:</p>
      <ul>
        <li v-for="author in modernAuthors" :key="author.id">
          {{ author.name }} ({{ author.birthYear }})
        </li>
      </ul>

      <h3>Mapping Arrays</h3>
      <p>Famous works:</p>
      <ul>
        <!-- Activity 8: Render a list of all famous works. Hint: Use the v-for directive to iterate through the array of authors that you have filtered out. -->
        <li v-for="work in allFamousWorks" :key="work">
          {{ work }}
        </li>
      </ul>

      <h3>Finding in Arrays</h3>
      <p>Finding by property: {{ orwell?.name }}</p>

      <h3>Nested Arrays/Objects</h3>
      <p>{{ austen?.name }}'s works:</p>
      <!-- Activity 9: Render a list of Austen's works. Hint: Use the v-for directive to iterate through the array of authors that you have filtered out. -->
      <ul>
        <li v-for="work in austen?.famousWorks" :key="work.title">
          {{ work.title }} ({{ work.year }})
        </li>
      </ul>
    </section>

    <section class="lab-section">
      <h2>🏢 Working with JSON Objects</h2>
      <p>Our <code>bookstores.json</code> is a JSON object.</p>

      <h3>Accessing Properties</h3>
      <p>
        Company:
        <!-- Activity 9a: Get the company name from the bookstores object. -->
        {{ bookstores.name }}
      </p>

      <p>
        Total Stores:
        <!-- Activity 9b: Get the total number of stores from the bookstores object. -->
        {{ bookstores.totalStores }}
      </p>

      <h3>Iterating Object Properties</h3>
      <p>Store Types:</p>
      <!-- Activity 10: Iterate through the storeTypes array and display the store type and the number of stores that use that type. -->
      <ul>
        <li v-for="(count, type) in bookstores.storeTypes" :key="type">
          {{ type }}: {{ count }} stores
        </li>
      </ul>

      <h3>Nested Objects</h3>
      <p>Opening Hours:</p>
      <!-- Activity 11: Iterate through the openingHours object and display the day of the week and the opening and closing times. -->
      <ul>
        <li v-for="(hours, day) in bookstores.openingHours" :key="day">
          {{ day }}: {{ hours.open }} - {{ hours.close }}
        </li>
      </ul>

      <h3>Working with Arrays in Objects</h3>
      <!-- Activity 12: Get the top sellers from the bookstores object. -->
      <p>We operate in: {{ bookstores.countries.join(', ') }}</p>
      <p>Our #1 seller: {{ bookstores.topSellers[0] }}</p>
    </section>

    <section class="lab-section">
      <h2>v-if & v-else</h2>
      <p>Toggle visibility based on a condition.</p>
      <!-- Activity 13: Toggle the message visibility when the button is clicked. -->
      <button @click="showMessage = !showMessage">Toggle Message</button>
      <p v-if="showMessage" class="message success">✨ You're a Vue superstar! ✨</p>
      <p v-else>Click the button to see a message.</p>
    </section>

    <section class="lab-section">
      <h2>Attribute, Class and Style Binding with <code>v-bind</code></h2>
      <p>Highlighting Specific Authors:</p>

      <!-- EFOLIO TASK 2.2: George Orwell Highlight -->
      <h3>🎯 TASK 2.2: George Orwell Highlight</h3>
      <p>Demonstrating attribute, class and style bindings for George Orwell:</p>

      <button @click="highlightOrwell = !highlightOrwell"
              class="orwell-toggle"
              style="background: linear-gradient(45deg, #ff6b6b, #ff4757) !important; color: white !important;">
        {{ highlightOrwell ? 'Remove' : 'Add' }} George Orwell Highlight
      </button>

      <p><strong>Debug:</strong> highlightOrwell = {{ highlightOrwell }}</p>

      <div class="orwell-demo">
        <div v-for="author in authors"
             :key="`orwell-${author.id}`"
             class="author-demo-card"
             :class="{
               'orwell-highlight': author.name === 'George Orwell' && highlightOrwell,
               'normal-author': author.name !== 'George Orwell' || !highlightOrwell
             }"
             :style="{
               backgroundColor: author.name === 'George Orwell' && highlightOrwell ? '#ff6b6b !important' : '#f8f9fa',
               color: author.name === 'George Orwell' && highlightOrwell ? 'white !important' : '#333',
               fontWeight: author.name === 'George Orwell' ? 'bold' : 'normal',
               border: author.name === 'George Orwell' && highlightOrwell ? '3px solid #ff4757' : '1px solid #ddd',
               transform: author.name === 'George Orwell' && highlightOrwell ? 'scale(1.05)' : 'scale(1)',
               boxShadow: author.name === 'George Orwell' && highlightOrwell ? '0 8px 25px rgba(255, 107, 107, 0.6)' : '0 2px 5px rgba(0,0,0,0.1)',
               transition: 'all 0.5s ease'
             }"
             :data-author-name="author.name"
             :data-is-orwell="author.name === 'George Orwell'"
             :data-birth-year="author.birthYear"
             :title="author.name === 'George Orwell' ? 'This is George Orwell - Author of 1984!' : `Author: ${author.name}`"
             :id="`author-highlight-${author.id}`">

          <div class="author-info">
            <h4>{{ author.name }}</h4>
            <p>Born: {{ author.birthYear }}</p>
            <p>Genres: {{ author.genres.join(', ') }}</p>
            <span v-if="author.name === 'George Orwell'" class="orwell-badge">🏆 Featured Author</span>
            <span v-if="author.name === 'George Orwell' && highlightOrwell" class="highlight-indicator">✨ HIGHLIGHTED!</span>
          </div>
        </div>
      </div>

      <!-- Original binding examples -->
      <h3>Class Binding</h3>
      <ul>
        <li v-for="author in authors"
            :key="author.id"
            :class="{ highlight: author.birthYear > 1850 }">
          {{ author.name }} ({{ author.birthYear }})
        </li>
      </ul>

      <!-- Dynamic style binding -->
      <h3>Style Binding</h3>
      <p>Toggle author highlight:</p>
      <button @click="highlightModernAuthors = !highlightModernAuthors">
        {{ highlightModernAuthors ? 'Hide' : 'Show' }} Modern Authors
      </button>
      <ul>
        <li v-for="author in authors"
            :key="`style-${author.id}`"
            :style="{
              backgroundColor: highlightModernAuthors && author.birthYear > 1850 ? '#42b883' : '#f0f0f0',
              color: highlightModernAuthors && author.birthYear > 1850 ? 'white' : '#333',
              fontWeight: author.name === 'George Orwell' ? 'bold' : 'normal',
              padding: '10px',
              margin: '5px 0',
              borderRadius: '5px',
              transition: 'all 0.3s ease'
            }">
          {{ author.name }} - {{ author.genres.join(', ') }}
        </li>
      </ul>

      <!-- Attribute binding -->
      <h3>Attribute Binding</h3>
      <p>Dynamic links and attributes:</p>
      <div v-for="author in authors" :key="`link-${author.id}`" class="author-card">
        <a :href="`#${author.name.toLowerCase().replace(' ', '-')}`"
           :id="`author-${author.id}`"
           :title="`Click to jump to ${author.name}`">
          {{ author.name }}
        </a>
        <span :data-birth-year="author.birthYear">({{ author.birthYear }})</span>
      </div>
    </section>
  </div>
</template>

<script setup>
import { ref, computed } from "vue"

// Activity 1: Import JSON files (authors.json and bookstores.json)
import authors from "../assets/json/authors.json"
import bookstores from "../assets/json/bookstores.json"

const showMessage = ref(false)
const highlightModernAuthors = ref(false)
const highlightOrwell = ref(false)

// Activity 2: Get authors born after 1850
const modernAuthors = computed(() => {
  return authors.filter(author => author.birthYear > 1850)
})

// Activity 3: Get all famous works
const allFamousWorks = computed(() => {
  return authors.flatMap(author => author.famousWorks.map(work => work.title))
})

// Activity 4: Find author by name
const orwell = computed(() => {
  return authors.find(author => author.name === "George Orwell")
})

// Activity 5: Find author by ID
const austen = computed(() => {
  return authors.find(author => author.id === 1)
})
</script>

<style scoped>
.json-lab {
  font-family: "Segoe UI", Tahoma, Geneva, Verdana, sans-serif;
  max-width: 80vw;
  margin: 0 auto;
  padding: 20px;
  background-color: #f4f4f4;
  border-radius: 10px;
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
  color: #333;
}

/* Dark mode support */
@media (prefers-color-scheme: dark) {
  .json-lab {
    background-color: #1a1a1a;
    color: #e0e0e0;
  }

  .lab-section {
    background-color: #2d2d2d !important;
    color: #e0e0e0;
  }

  h1, h2, h3, p {
    color: #e0e0e0 !important;
  }

  code {
    background-color: #404040 !important;
    color: #e0e0e0 !important;
  }

  li {
    background-color: #404040 !important;
    color: #e0e0e0 !important;
  }

  .author-card {
    background-color: #404040 !important;
  }

  .author-card a {
    color: #6dd4a8 !important;
  }

  .author-demo-card {
    background-color: #34495e !important;
    color: #ecf0f1 !important;
  }

  .author-info h4, .author-info p {
    color: #ecf0f1 !important;
  }
}

h1,
h2 {
  color: #333;
}
h1 {
  text-align: center;
}

.lab-section {
  background-color: white;
  padding: 20px;
  margin-bottom: 20px;
  border-radius: 8px;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
}

.message {
  padding: 10px;
  border-radius: 5px;
  margin-top: 10px;
}

.success {
  background-color: #e7faf3;
  color: #42b883;
  border: 1px solid #42b883;
}

.highlight {
  background-color: #42b883;
  color: white;
}

code {
  background-color: #e0e0e0;
  padding: 2px 5px;
  border-radius: 4px;
  font-family: "Courier New", Courier, monospace;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  background-color: #f0f0f0;
  padding: 10px;
  margin: 5px 0;
  border-radius: 5px;
}

button {
  padding: 10px 15px;
  background-color: #42b883;
  color: white;
  border: none;
  border-radius: 5px;
  cursor: pointer;
  font-size: 14px;
}

button:hover {
  background-color: #369970;
}

.author-card {
  display: flex;
  align-items: center;
  gap: 10px;
  margin: 10px 0;
  padding: 10px;
  background-color: #f9f9f9;
  border-radius: 5px;
}

.author-card a {
  text-decoration: none;
  color: #42b883;
  font-weight: bold;
}

.author-card a:hover {
  text-decoration: underline;
}

/* EFOLIO TASK 2.2: George Orwell Highlight Styles */
.orwell-toggle {
  background: linear-gradient(45deg, #ff6b6b, #ff4757) !important;
  color: white !important;
  border: none !important;
  padding: 12px 20px;
  border-radius: 25px;
  cursor: pointer;
  font-size: 16px;
  font-weight: bold;
  margin-bottom: 20px;
  transition: all 0.3s ease;
  box-shadow: 0 4px 15px rgba(255, 107, 107, 0.3);
}

.orwell-toggle:hover {
  transform: translateY(-2px) !important;
  box-shadow: 0 6px 20px rgba(255, 107, 107, 0.4) !important;
  background: linear-gradient(45deg, #ff5252, #ff3742) !important;
}

.orwell-demo {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
  gap: 15px;
  margin: 20px 0;
}

.author-demo-card {
  padding: 20px;
  border-radius: 10px;
  transition: all 0.5s ease;
  cursor: pointer;
}

.author-demo-card:hover {
  transform: translateY(-3px) !important;
}

.orwell-highlight {
  animation: orwellGlow 2s ease-in-out infinite alternate;
}

@keyframes orwellGlow {
  from {
    box-shadow: 0 8px 25px rgba(255, 107, 107, 0.4);
  }
  to {
    box-shadow: 0 12px 35px rgba(255, 107, 107, 0.7);
  }
}

.normal-author {
  opacity: 0.7;
}

.orwell-highlight .normal-author {
  opacity: 1;
}

.author-info h4 {
  margin: 0 0 10px 0;
  font-size: 1.2rem;
}

.author-info p {
  margin: 5px 0;
  font-size: 0.9rem;
}

.orwell-badge {
  display: inline-block;
  background: linear-gradient(45deg, #ffd700, #ffed4e);
  color: #333;
  padding: 4px 8px;
  border-radius: 12px;
  font-size: 0.8rem;
  font-weight: bold;
  margin-top: 10px;
}

.highlight-indicator {
  display: inline-block;
  background: linear-gradient(45deg, #ff6b6b, #ff4757);
  color: white;
  padding: 4px 8px;
  border-radius: 12px;
  font-size: 0.8rem;
  font-weight: bold;
  margin-top: 5px;
  margin-left: 5px;
  animation: pulse 1.5s ease-in-out infinite;
}

@keyframes pulse {
  0%, 100% { opacity: 1; }
  50% { opacity: 0.7; }
}
</style>

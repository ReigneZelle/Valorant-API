<template>
    <div id="master-wrap">
        <img src="~src/assets/background.png" class="background-image" />
        <div class="content-container">
            <div class="navbar">
                <router-link to="/home" class="nav-link">HOME</router-link>
                <a href="minigame.html" class="nav-link">MINIGAME</a>
                <a class="nav-link" href="/login">LOGOUT</a> <!-- Logout Button -->
            </div>
            <h1 class="header">What is Valorant?</h1>
            <div class="info">
                <p>
                    Valorant is a free-to-play first-person hero shooter developed and
                    published by Riot Games. Each player selects an agent to play in a 5v5
                    battle. Each agent has their own role, so you must work together with
                    your team to win. The first team to win 13 rounds wins the game.
                </p>
            </div>
            <div>
                <h1 class="game">GAMEPLAY</h1>
            </div>
            <div class="video">
                <iframe width="800" height="450" src="https://www.youtube.com/embed/auNpqGG0Ns8"
                    title="YouTube video player" frameborder="0"
                    allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
                    allowfullscreen></iframe>
            </div>
            <h1 class="header">Other</h1>
            <button v-if="!showAgentsList" class="viewagent" @click="showAgents">VIEW ALL AGENTS</button>
            <button v-else class="viewagent" @click="toggleAgentsList">HIDE AGENTS</button>
            <button v-if="!showMapsList" class="viewmaps" @click="showMaps">VIEW ALL MAPS</button>
            <button v-else class="viewmaps" @click="toggleMapsList">HIDE MAPS</button>


            <div class="agents-list" v-if="showAgentsList">
                <ul>
                    <li v-for="agent in agents" :key="agent.uuid">
                        <div class="agent-item" @click="showAgentDescription(agent)">
                            <div class="agent-icon">
                                <img :src="agent.displayIcon" alt="Agent Icon" />
                            </div>
                            <p>{{ agent.displayName }}</p>
                        </div>
                    </li>
                </ul>
            </div>

            <div v-if="showAgentModal" class="agent-modal">
  <div class="modal-content">
    <span class="close" @click="closeAgentModal">&times;</span>
    <h2>{{ selectedAgent.displayName }}</h2>
    <p v-if="selectedAgent.description">{{ selectedAgent.description }}</p>
    <p v-else>No description available</p>
  </div>
</div>

            <div class="maps-list" v-if="showMapsList">
                <ul>
                    <li v-for="map in maps" :key="map.uuid">
                        <div class="map-item">
                            <div class="map-icon">
                                <img :src="map.listViewIcon" alt="Map Icon" />
                            </div>
                            <p>{{ map.displayName }}</p>
                        </div>
                    </li>
                </ul>
            </div>

            <div class="footer">
                <p>© 2023 Valorant. All rights reserved.</p>
            </div>
        </div>
    </div>
</template>
  
<style lang="scss" scoped>
.navbar {
    display: flex;
    justify-content: center;
    background-color: #1C1D21;
    padding: 10px 0;
}

.nav-link {
    font-size: 18px;
    color: white;
    text-align: center;
    font-family: "Arial", sans-serif;
    padding: 10px 20px;
    text-decoration: none;
    border-bottom: 3px solid transparent;
    transition: all 0.3s;
    margin: 0 10px;
}

.nav-link:hover {
    border-bottom: 3px solid #ff8fa3;
    letter-spacing: 2px;
}

body {
    background-color: #e56b6f;
    -webkit-background-size: cover;
    -moz-background-size: cover;
    -o-background-size: cover;
    background-size: cover;
}

.header {
    font-size: 100px;
    font-family: "Arial", sans-serif;
    text-align: center;
    color: #f08080;
    cursor: pointer;
    transition: all 0.5s;
    text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.4);
    margin-bottom: 50px;
}

.header:hover {
    color: #ff8fa3;
    letter-spacing: 8px;
}

.game {
    font-size: 100px;
    font-family: monospace;
    text-align: center;
    color: #f08080;
    cursor: pointer;
    margin-top: 400px;
    transition: all 0.5s;
}

.game:hover {
    color: #ff8fa3;
    letter-spacing: 8px;
}

p {
    font-family: monospace;
    color: white;
    text-align: center;
    font-size: 20px;
}

.video {
    display: flex;
    flex-direction: column;
    align-items: center;
    top: 500px;
}

.info {
    position: absolute;
    top: 300px;
    font-size: 35px;
    left: 620px;
    background-color: transparent;
    width: 600px;
    text-align: center;
    border-radius: 30px;
    padding: 30px;
    border-right: 1px solid #222;
    text-align: center;
    float: left;
    cursor: pointer;
    transition: all 1.8s;
}

.info:hover {
    background-color: #adb5bd;
    color: black;
}

.viewagent {
    border: 3px solid white;
    font-size: 18px;
    outline: 0;
    display: inline-block;
    padding: 15px 50px;
    color: white;
    background-color: transparent;
    text-align: center;
    cursor: pointer;
    font-family: MONOSPACE;
    font-weight: 600;
    transition: all 0.5s;
    margin-left: 31%;
}

button:hover {
    background-color: white;
    color: black;
    letter-spacing: 3px;
}

.viewmaps {
    border: 3px solid white;
    font-size: 18px;
    outline: 0;
    display: inline-block;
    padding: 15px 50px;
    color: white;
    background-color: transparent;
    text-align: center;
    cursor: pointer;
    font-family: MONOSPACE;
    font-weight: 600;
    transition: all 0.5s;
    margin-left: 200px;
}

.content-container {
    position: relative;
}

.background-image {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    z-index: -1;
}

.footer {
    text-align: center;
    margin-top: 50px;
    color: white;
    font-family: "Arial", sans-serif;
    font-size: 16px;
}

.agents-list {
    margin-top: 50px;
    text-align: center;
}

.agents-list ul {
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
    list-style: none;
    padding: 0;
    margin: 0;
}

.agents-list li {
    flex: 0 0 20%;
    max-width: 20%;
    padding: 20px;
}

.agents-list img {
    display: block;
    width: 100%;
    max-height: 100px;
    margin: 0 auto;
    border-radius: 50%;
    box-shadow: 0 2px 4px rgba(0, 0, 0, 0.2);
}

.agents-list p {
    color: white;
    font-size: 18px;
    font-weight: bold;
    margin-top: 10px;
}

.agent-item {
    display: inline-block;
    margin: 10px;
    text-align: center;
}

.agent-icon {
    width: 100px;
    height: 100px;
    border-radius: 50%;
    overflow: hidden;
    box-shadow: 0 2px 4px rgba(0, 0, 0, 0.2);
    border: 3px solid #ff8fa3;
    /* Add the border property here */
}

.agent-icon img {
    display: block;
    width: 100%;
    height: 100%;
    object-fit: cover;
}
.agent-modal {
  display: none; /* Change "none" to "flex" */
  justify-content: center;
  align-items: center;
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.8);
  z-index: 9999;
}
.modal-content {
    max-width: 500px;
    padding: 20px;
    background-color: #fff;
    border-radius: 5px;
    box-shadow: 0 0 10px rgba(0, 0, 0, 0.2);
    position: relative;
}

.close {
    position: absolute;
    top: 10px;
    right: 10px;
    cursor: pointer;
    font-size: 20px;
}

.agent-modal {
    display: flex;
    justify-content: center;
    align-items: center;
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background-color: rgba(0, 0, 0, 0.8);
    z-index: 9999;
}

.modal-content {
    max-width: 500px;
    padding: 20px;
    background-color: #fff;
    border-radius: 5px;
    box-shadow: 0 0 10px rgba(0, 0, 0, 0.2);
    position: relative;
}

.close {
    position: absolute;
    top: 10px;
    right: 10px;
    cursor: pointer;
    font-size: 20px;
}

.agent-modal h2 {
    font-size: 24px;
    font-weight: bold;
    margin-bottom: 10px;
}

.agent-modal p {
    font-size: 18px;
    line-height: 1.6;
}

.maps-list {
    margin-top: 50px;
    text-align: center;
}

.maps-list ul {
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
    list-style: none;
    padding: 0;
    margin: 0;
}

.maps-list li {
    flex: 0 0 20%;
    max-width: 20%;
    padding: 20px;
}

.maps-list img {
    display: block;
    width: 100%;
    height: auto;
    max-height: 100px;
    margin: 0 auto;
    box-shadow: 0 2px 4px rgba(0, 0, 0, 0.2);
}

.maps-list p {
    color: white;
    font-size: 18px;
    font-weight: bold;
    margin-top: 10px;
}

.map-item {
    display: inline-block;
    margin: 10px;
    text-align: center;
}

.map-icon {

    height: 100px;
    overflow: hidden;
    box-shadow: 0 2px 4px rgba(0, 0, 0, 0.2);
    border: 3px solid #ff8fa3;
    /* Add the border property here */
}

.map-icon img {
    display: block;
    width: 100%;
    height: 100%;
    object-fit: cover;
}
</style>

<script>
import { defineComponent } from 'vue';

export default defineComponent({
    name: 'HomePage',
    data() {
        return {
            showAgentsList: false,
            agents: [],
            showMapsList: false,
            maps: [],
            showAgentModal: false, // Initialize showAgentModal to false
            selectedAgent: null,
        };
    },
    methods: {
        async showAgents() {
            try {
                const response = await this.$axios.get('https://valorant-api.com/v1/agents');
                const agents = response.data.data.map((agent) => ({
                    ...agent,
                    health: 100,
                    armor: 50,
                }));
                this.agents = agents.filter((agent) => agent.isPlayableCharacter);
                this.showAgentsList = true;
                console.log(this.agents); // Add this line to check the agents data
            } catch (error) {
                console.error(error);
            }
        },
        async showMaps() {
            try {
                const response = await this.$axios.get('https://valorant-api.com/v1/maps');
                this.maps = response.data.data;
                this.showMapsList = true;
            } catch (error) {
                console.error(error);
            }
        },
        toggleAgentsList() {
            this.showAgentsList = !this.showAgentsList;
        },
        toggleMapsList() {
            this.showMapsList = !this.showMapsList;
        },
        showAgentDescription(agent) {
  this.selectedAgent = agent;
  console.log(this.selectedAgent.description); // Add this line to check the description
  this.showAgentModal = true;
},
        closeAgentModal() {
            this.showAgentModal = false;
        },
    },
});
</script>
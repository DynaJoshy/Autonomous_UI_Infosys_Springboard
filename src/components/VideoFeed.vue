<template>
<<<<<<< HEAD
  <div class="main-container">
    <!-- Title and Navigation Section -->
    <div class="title-section">
      <h1 style="font-size: 1.5em;color:whitesmoke;">Infosys Springboard Internship : 5.0</h1>
      <nav class="nav-bar">
        <router-link to="/" class="nav-link">Home</router-link>
        <router-link to="/about" class="nav-link">About</router-link>
        <router-link to="/timeline" class="nav-link">Timeline</router-link>
        <router-link to="/contact" class="nav-link">Contact</router-link>
      </nav>
    </div>

    <!-- Main Content Container -->
    <div class="content-wrapper">
      <div class="container">
        <!-- Left Side: UI Section -->
        <div class="ui-section">
          <div class="video-monitor">
            <!-- <h3>Video Feed</h3> -->
            <div class="monitor-frame">
              <div class="monitor-screen">
                <template v-if="isRealTime">
                  <p>Streaming real-time video...</p>
                </template>
                <template v-else>
                  <p>Live video from the autonomous vehicle's camera will be displayed here.</p>
                </template>
              </div>
              <div class="monitor-stand"></div>
            </div>

            <!-- Video Upload or Real-Time Video Toggle -->
            <div class="upload-section">
              <button @click="toggleVideoMode" class="toggle-button">
                Switch to {{ isRealTime ? 'Upload Video' : 'Real-Time Video' }}
              </button>
              <template v-if="!isRealTime">
                <label for="video-upload" class="upload-button">
                  Upload Video
                  <input
                    type="file"
                    id="video-upload"
                    accept="video/*"
                    @change="handleVideoUpload"
                    hidden
                  />
                </label>
                <p v-if="uploadedVideo" class="uploaded-video-name">
                  Uploaded: {{ uploadedVideo }}
                </p>
              </template>
            </div>
          </div>

          <!-- Decisions Monitor -->
          <div class="decision-monitor">
            <h3>Decisions</h3>
            <p class="decision-item">{{ currentDecision }}</p>
          </div>
        </div>

        <!-- Right Side: Background Video -->
        <div class="background-section">
          <video
            v-if="backgroundVideo"
            :src="backgroundVideo"
            autoplay
            loop
            muted
            class="background-video"
            @error="handleVideoError"
          ></video>
          <template v-else>
            <div class="placeholder">
              <p>{{ videoErrorMessage || 'No background video uploaded.' }}</p>
            </div>
          </template>
        </div>
      </div>
=======
  <div class="container">
    <!-- Left Side: UI Section -->
    <div class="ui-section">
      <div class="video-monitor">
        <h3>Video Feed</h3>
        <div class="monitor-frame">
          <div class="monitor-screen">
            <template v-if="isRealTime">
              <p>Streaming real-time video...</p>
            </template>
            <template v-else>
              <p>
                Live video from the autonomous vehicle's camera will be
                displayed here.
              </p>
            </template>
          </div>
          <div class="monitor-stand"></div>
        </div>

        <!-- Video Upload or Real-Time Video Toggle -->
        <div class="upload-section">
          <button @click="toggleVideoMode" class="toggle-button">
            Switch to {{ isRealTime ? 'Upload Video' : 'Real-Time Video' }}
          </button>
          <template v-if="!isRealTime">
            <label for="video-upload" class="upload-button">
              Upload Video
              <input
                type="file"
                id="video-upload"
                accept="video/*"
                @change="handleVideoUpload"
                hidden
              />
            </label>
            <p v-if="uploadedVideo" class="uploaded-video-name">
              Uploaded: {{ uploadedVideo }}
            </p>
          </template>
        </div>
      </div>

      <!-- Decisions Monitor -->
      <div class="decision-monitor">
        <h3>Decisions</h3>
        <p class="decision-item">
          {{ currentDecision }}
        </p>
      </div>
    </div>

    <!-- Right Side: Background Video -->
    <div class="background-section">
      <video
        v-if="backgroundVideo"
        :src="backgroundVideo"
        autoplay
        loop
        muted
        class="background-video"
      ></video>
      <template v-else>
        <div class="placeholder">
          <p>No background video uploaded.</p>
        </div>
      </template>
>>>>>>> 6d5f6ae90a50e1521fe0c8a89f6b0b022afb2050
    </div>
  </div>
</template>

<script>
<<<<<<< HEAD
// Try importing the video file with error handling
let backgroundVideoFile;
try {
  backgroundVideoFile = require('../public/Car.mp4');
} catch (error) {
  console.warn('Default video file not found:', error);
  backgroundVideoFile = null;
}
=======
import backgroundVideoFile from '../assets/car.mp4';
>>>>>>> 6d5f6ae90a50e1521fe0c8a89f6b0b022afb2050

export default {
  name: 'VideoFeed',
  data() {
    return {
<<<<<<< HEAD
      uploadedVideo: null,
=======
      uploadedVideo: null, // Name of the uploaded video file
>>>>>>> 6d5f6ae90a50e1521fe0c8a89f6b0b022afb2050
      decisions: [
        'Detecting obstacles on the road...',
        'Slowing down due to traffic ahead...',
        'Changing lanes to avoid collision...',
        'Adjusting speed to match traffic flow...',
        'Monitoring vehicle surroundings...',
        'Identifying traffic lights...',
        'Detecting pedestrians nearby...',
        'Calculating alternate route...',
        'Engaging emergency brakes...',
        'Resuming normal speed...',
      ],
<<<<<<< HEAD
      currentDecisionIndex: 0,
      isRealTime: false,
      backgroundVideo: backgroundVideoFile,
      videoErrorMessage: null,
      decisionInterval: null
=======
      currentDecisionIndex: 0, // Index of the currently displayed decision
      isRealTime: false, // Toggle between video upload and real-time video
      backgroundVideo: backgroundVideoFile, // URL of the uploaded video
>>>>>>> 6d5f6ae90a50e1521fe0c8a89f6b0b022afb2050
    };
  },
  computed: {
    currentDecision() {
      return this.decisions[this.currentDecisionIndex];
    },
  },
  methods: {
    handleVideoUpload(event) {
      const file = event.target.files[0];
      if (file) {
<<<<<<< HEAD
        try {
          this.uploadedVideo = file.name;
          this.backgroundVideo = URL.createObjectURL(file);
          this.videoErrorMessage = null;
        } catch (error) {
          console.error('Error uploading video:', error);
          this.videoErrorMessage = 'Error uploading video. Please try again.';
        }
=======
        this.uploadedVideo = file.name;
        this.backgroundVideo = URL.createObjectURL(file); // Set video as background
>>>>>>> 6d5f6ae90a50e1521fe0c8a89f6b0b022afb2050
      }
    },
    toggleVideoMode() {
      this.isRealTime = !this.isRealTime;
    },
    cycleDecisions() {
<<<<<<< HEAD
      this.currentDecisionIndex = (this.currentDecisionIndex + 1) % this.decisions.length;
    },
    handleVideoError(error) {
      console.error('Video error:', error);
      this.videoErrorMessage = 'Error playing video. Please try again.';
      this.backgroundVideo = null;
    },
    startDecisionCycle() {
      this.decisionInterval = setInterval(this.cycleDecisions, 3000);
    },
    stopDecisionCycle() {
      if (this.decisionInterval) {
        clearInterval(this.decisionInterval);
      }
    }
=======
      this.currentDecisionIndex =
        (this.currentDecisionIndex + 1) % this.decisions.length;
    },
  },
  mounted() {
    // Cycle through decisions every 3 seconds
    setInterval(this.cycleDecisions, 3000);
>>>>>>> 6d5f6ae90a50e1521fe0c8a89f6b0b022afb2050
  },
  mounted() {
    this.startDecisionCycle();
  },
  beforeUnmount() {
    this.stopDecisionCycle();
  }
};
</script>

<style scoped>
<<<<<<< HEAD
.main-container {
  min-height: 100vh;
  background-color: #121212;
  padding-top: 80px;
}

.title-section {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  background-color: #1a1a1a;
  padding: 15px 0;
  text-align: center;
  z-index: 100;
  box-shadow: 0 2px 4px rgba(0,0,0,0.2);
}

.nav-bar {
  display: flex;
  justify-content: center;
  gap: 20px;
  padding: 10px 0;
}

.nav-link {
  color: white;
  text-decoration: none;
  padding: 8px 16px;
  border-radius: 4px;
  transition: all 0.3s ease;
}

.nav-link:hover {
  background-color: #333;
}

.router-link-active {
  background-color: #4CAF50;
}

.content-wrapper {
  height: calc(100vh - 80px);
  overflow: hidden;
}

.container {
  display: flex;
  width: 100%;
  height: 100%;
=======
/* Global Styles to Remove Any Default Margin or Padding */

/* Main Container */
.container {
  display: flex;
  flex-direction: row;
  width: 100vw;
  height: 100vh;
  margin: 0;
  padding: 0;
  box-sizing: border-box;
>>>>>>> 6d5f6ae90a50e1521fe0c8a89f6b0b022afb2050
}

.ui-section {
  flex: 1;
  padding: 20px;
  background-color: #121212;
  display: flex;
  flex-direction: column;
  gap: 20px;
  color: white;
  overflow: auto;
}

<<<<<<< HEAD
=======
/* Right Side: Background Video Section */
>>>>>>> 6d5f6ae90a50e1521fe0c8a89f6b0b022afb2050
.background-section {
  flex: 1;
  display: flex;
  justify-content: center;
  align-items: center;
  background-color: #000;
  position: relative;
  overflow: hidden;
}

<<<<<<< HEAD
=======
.background-video {
  width: 100%;
  height: 100%;
  object-fit: cover;
}

.placeholder {
  display: flex;
  justify-content: center;
  align-items: center;
  color: #888;
  font-size: 18px;
}

/* Video Monitor */
>>>>>>> 6d5f6ae90a50e1521fe0c8a89f6b0b022afb2050
.video-monitor {
  background: linear-gradient(145deg, #222, #333);
  border-radius: 12px;
  padding: 20px;
<<<<<<< HEAD
  margin-top:20px;
=======
  display: flex;
  flex-direction: column;
  align-items: center;
>>>>>>> 6d5f6ae90a50e1521fe0c8a89f6b0b022afb2050
}

.monitor-frame {
  width: 100%;
  max-width: 600px;
  margin: 0 auto;
  background: #333;
  border: 6px solid #444;
  border-radius: 12px;
  box-shadow: 0 8px 16px rgba(0, 0, 0, 0.8);
}

.monitor-screen {
  width: 100%;
  height: 300px;
  background: #111;
  display: flex;
  justify-content: center;
  align-items: center;
  color: #888;
<<<<<<< HEAD
  padding: 20px;
  text-align: center;
=======
  font-size: 16px;
  text-align: center;
  border-radius: 4px;
>>>>>>> 6d5f6ae90a50e1521fe0c8a89f6b0b022afb2050
}

.monitor-stand {
  width: 80px;
  height: 20px;
  background: #444;
  margin: 10px auto 0;
  border-radius: 4px;
<<<<<<< HEAD
=======
}
.upload-section {
  margin-top: 30px;  /* बटन को नीचे की तरफ खिसकाने के लिए मार्जिन जोड़ा */
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 10px;  /* बटन्स के बीच स्पेसिंग */
}

/* Toggle Button */
.toggle-button {
  background-color: #555;
  color: #fff;
  padding: 10px 20px;
  border: none;
  border-radius: 8px;
  cursor: pointer;
}


.toggle-button:hover {
  background-color: #666;
>>>>>>> 6d5f6ae90a50e1521fe0c8a89f6b0b022afb2050
}

.upload-section {
  margin-top: 20px;
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 10px;
}

.toggle-button, .upload-button {
  background-color: #4CAF50;
  color: white;
  padding: 10px 20px;
  border: none;
  border-radius: 4px;
  cursor: pointer;
  transition: background-color 0.3s;
}

.toggle-button:hover, .upload-button:hover {
  background-color: #45a049;
}

.decision-monitor {
  background: linear-gradient(145deg, #222, #333);
  border-radius: 12px;
  padding: 20px;
<<<<<<< HEAD
}

.background-video {
  width: 100%;
  height: 100%;
  object-fit: cover;
}

.placeholder {
  color: #666;
  text-align: center;
  padding: 20px;
}

.uploaded-video-name {
  color: #4CAF50;
  font-size: 0.9em;
=======
  text-align: center;
  font-size: 18px;
  color: #ddd;
}

/* Custom Scrollbar Styling */
.ui-section::-webkit-scrollbar {
  width: 8px;
}

.ui-section::-webkit-scrollbar-track {
  background: #1a1a1a;
  border-radius: 4px;
}

.ui-section::-webkit-scrollbar-thumb {
  background: #444;
  border-radius: 4px;
  transition: background 0.3s ease;
}

.ui-section::-webkit-scrollbar-thumb:hover {
  background: #666;
}

/* Firefox के लिए स्क्रॉलबार स्टाइलिंग */
.ui-section {
  scrollbar-width: thin;
  scrollbar-color: #444 #1a1a1a;
>>>>>>> 6d5f6ae90a50e1521fe0c8a89f6b0b022afb2050
}
</style>
<template>
  <div class="home">
    <h1>Band Name Machine</h1>

    <div class="control-panel">
      <div class="amp-knob">
        <label id="select-genre" for="genre">Genre:</label>
        <div class="dropdown-options">
          <select class="make-dropdown" id="genre" v-model="selectedGenre">
            <option value="bluegrass">Bluegrass</option>
            <option value="blues">Blues</option>
            <option value="country">Country</option>
            <option value="funk">Funk</option>
            <option value="heavymetal">Heavy Metal</option>
            <option value="jazz">Jazz</option>
            <option value="pop">Pop</option>
            <option value="punk">Punk</option>
            <option value="reggae">Reggae</option>
            <option value="rock">Rock</option>
          </select>
        </div>
      </div>

      <div class="amp-knob">
        <label id="select-words" for="words">Words:</label>
        <div class="dropdown-options">
          <select class="make-dropdown" id="words">
            <option value="one">1</option>
            <option value="two">2</option>
            <option value="three">3</option>
          </select>
        </div>
      </div>

      <div class="amp-knob">
        <label id="select-spicy" for="spicy">Spicy Level:</label>
        <div class="dropdown-options">
          <select class="make-dropdown" id="spicy">
            <option value="mild">Mild</option>
            <option value="medium">Medium</option>
            <option value="extra">Extra Spicy</option>
          </select>
        </div>
      </div>
    </div>

    <button @click="generateName" type="submit">GENERATE BAND NAME</button>
    <div id="band-name-container">
      <input type="text" v-model="generatedName" id="band-name-display" readonly />
    </div>
  </div>
</template>

<script>
// @ is an alias to /src
import HelloWorld from '@/components/HelloWorld.vue'

export default {
  name: 'HomeView',

  data() {
    return {

      adjectives: ["Bloated Steve", "Rusty", "Shady", "Rambling", "Wandering", "Dusty Steve", "Elton James", "Mellow", "Rapid Falls", "Muddy River", "Cloudy", "Mrs. Smith", "Uncle Larry's", "Flying", "Grumpy Dave", "Floating", "The River City", "Rockin Reggie", "Uma Thighmaster", "Savvy Sam", "Thundering", "Good Ole", "Interesting", "The Big Creek", "Flagrant", "The Steep Canyon", "Flaming Phil", "Rocky", "Sudden", "Grandpa Mustard", "Nell Diamond", "Urethra Franklin", "Unspoken", "Ginger Nutcracks", "Inversion", "Furious George", "Up Yours", "Silent", "Glacier Bob", "Sweaty Palms", "Paul Bunyan", "Saul Goodman", "Horny", "Soggy", "Saucy Mike"],
      nouns: ["and the Flatulent Five", "and the Ohio Seven", "and the Nevada Swingers", "and the Nutcrackers", "Fury", "Soy Explosion", "the Pinheads", "Mountain", "River", "Dream", "Shadow", "Storm", "Whisper", "Echo", "Thunder", "Blaze",
        "Voyage", "Journey", "Realm", "and his Stupid Empire", "Vision", "Voyager", "Maze", "Spectrum", "Rockers", "Drifters",
        "Mirror", "Goes to Phoenix", "Horizon", "Blues Masters", "Swingers", "Formation", "Rebels", "Cowboys", "Orchestra", "Fellers", "Labyrinth", "and the Gaping Chasm", "Beacon", "Vortex", "Pulse", "and the Quasar", "River", "Canyon",
        "Comet", "Crescent", "and Horny Harbor", "Ramblers", "and the Philly Phanatics", "Overtime", "and the Wafflers", "Quest", "Specter", "Cloud Formation", "Ark", "Nebula", "Oracle", "and the Eclipse", "Sandwich",
        "Fury", "Sanctuary", "and the Escape", "and the Girth Mountain Orchestra", "Cipher", "Delta", "and The Abyss", "Odyssey", "Response", "Experience", "Cipher", "Glacier", "Inferno"],

      selectedGenre: 'bluegrass',
      generatedName: '',


      genres: {
        bluegrass: {
          adjectives: ["Dry Gulch", "Ragged", "The Rancid Canyon", "Slim Pickin'", "Lonesome", "Lonesome Top", "Stumble Valley", "Grandpa Pants",
            "Foggy", "Big Creek", "The Mighty Wind", "Lonely Mountain",
            "Big Mountain", "Deep Canyon", "Muddy Creek", "Crooked Creek", "Lonesome Valley", "Stinky Canyon", "Front Porch", "Apple Cider", "Yonder",
            "Country", "Appalachian", "Smoky"],
          nouns: ["Ramblers", "Revival", "Ridge", "Creek", "Hollow", "Outhouse", "Jamboree", "Jubille", "Holler",
            "River", "Summit", "Mountain", "Hill", "Moonshine", "Wildflowers", "Ramblers", "Jubilee", "Woodpile",
            "Express", "Mountain", "Drifters", "Grasscutters", "Pickers", "Creek"],
          wildcards: ["The Rockin Fellars", "Buffalo Larry and the Girth Mountain Orchestra", "The Hay Bales",
            "Banjo Bonanza", "Uncle Elmer and the Grasscutters", "Lonesome Top Highway", "Slim Pickin' and the Mighty Wind",
            "Washboard Slim and the Peoria Playboys", "Grandpa Mustard and the Foggy Mountain Ramblers", "Pickin' Pete and the Kentucky Wildflowers"]

        },

        blues: {
          adjectives: ["Crossroads", "Blues", "Howlin' Matt", "Smoky Joe", "Deep", "Soulful Sam", "Swingin'", "Monday Morning",
            "Delta", "Cold", "Blue", "Deep", "Lowdown", "Dusty", "Crisp", "Slick", "Moanin'", "Juke", "Raw", "Burnin'", "Delta", "Rusty", "Jazzy", "Rollin'", "Wild",
            "Steady", "Sharp", "Twangy", "Faded", "The Blues", "Electric"],
          nouns: ["Cats", "Shouters", "and the Troubadours", "Experience", "Review", "Explosion", "Band", "Highway", "River",
            "and His Representatives", "Revue", "Kings", "Bluesmen", "Blues Busters", "River", "Soul", "Groove", "Trouble", "Crossroads", "Rhythm", "Mojo", "Shack",
            "Shadow", "Heart", "Whiskey", "Train", "Delta", "Cane", "Storm", "Shuffle", "Shack", "Road", "Smoke", "Guitar", "Riff", "Bluesmen", "Melody", "Night"],
          wildcards: ["Muddy Walter and the Mississippi Misfits", "Alabama Slim and Sizzlin' Bacon", "F'get About It", "Bucket of Blues", "Blues Explosion", "Sizzlin' Bacon and the Troubadours",]
        },

        country: {
          adjectives: ["Gritty", "Freewheelin'", "Tall", "Bold", "Timeless", "Hardy", "Sage", "Wide-Open", "Broken-Hearted", "Faithful", "Brave", "Wild - Eyed", "Grizzled", "Worn", "Honest",
            "Dirt-Road", "Steady", "Straight-Shooting", "Sharp", "Stubborn", "Rambling", "Solid", "Rugged", "True", "Galloping", "Desperado",
            "Buckaroo", "Buffalo", "Pioneer", "Outlaw", "Timber", "Creek", "Crossroads", "Cactus", "Bronco", "Horizon", "Frontier",
            "Windmill", "Barnyard", "Campfire", "Fence", "Spur", "Maverick", "Sky", "Field", "Horseshoe", "Cabin", "Hickory", "Sunset", "Dusty",
            "Wild", "Silver", "Lonely", "Golden", "Wandering", "Rusty", "Midnight", "Old", "Broken", "Blazing", "Whistling", "Roaring", "Shady",
            "Mighty", "Stormy", "Wide", "Rugged", "Whispering", "Crimson", "Winding", "Rolling", "Quiet", "Open", "High"],
          nouns: ["All-Stars", "Cowboys", "and the Flatulent Five", "and the Lonesome Drifters", "Prairie", "Trail", "Canyon", "Whiskey", "Coyote",
            "River", "Desert", "Barn", "Dust", "Cowboy", "Lasso", "Saddle", "Hill", "Moon", "Horse", "Range", "Ranch", "Oak", "Rider", "Thunder",
            "Meadow", "Valley", "Storm", "Tumbleweed", "Ridge", "Wagon"],
          wildcards: ["Dusty and the Freewheelers", "The Front-Porch All-Stars", "Stubborn Horseshoe", "The Rusty Spurs", "Buckaroo Bob and the Flatulent Five"]


        },

        funk: {
          adjectives: ["Funkadelic", "Jah", "Conscious", "Sonic", "Boom", "Cosmic", "Mega", "Super", "Giant", "Sonic", "Funky", "Smooth", "Electric", "Cosmic", "Groovy", "Sizzling", "Wavy", "Chill", "Vibrant", "Bouncy", "Slick", "Soulful", "Sizzling", "Radiant", "Liquid", "Deep", "Wild", "Hot", "Snappy", "Vibing", "Golden", "Velvet", "Lush", "Spicy", "Hypnotic"],
          nouns: ["Rockers", "Experience", "Jam", "Vortex", "Living", "Groove", "Vibe", "Rhythm", "Bassline", "Jam", "Funk", "Soul", "Beat", "Boogie", "Bounce", "Pulse", "Sizzle", "Sax", "Shakers", "Horn", "Flow", "Fusion", "Shuffle", "Keys", "Swagger", "Fever", "Crunch", "Chill", "Rocket", "Waves"]

        },

        heavymetal: {
          adjectives: ["Death", "Rancid", "Savage", "Primal", "Molten", "Destruction", "Sonic",
            "Decayed", "Rotten", "Flesh-Eating", "Vengeful", "Mega", "Super", "Giant", "Sonic"],
          nouns: ["Rockers", "Assassins", "Sandwich", "Distortion", "Vortex", "Nexus", "Void",
            "Spiral", "Rift", "Chasm", "Overlords", "Reaper", "Abyss", "Fury", "Skull", "Havoc",],
          wildcards: ["Grave Buffet", "Supersonic Gist", "Void Where Prohibited",]

        },

        jazz: {
          adjectives: ["Smooth", "Cool", "Blue", "Swingin'", "Mellow", "Velvet", "Hot", "Golden", "Deep", "Soulful",
            "Steady", "Sweet", "Sizzling", "Lush", "Lowdown", "Slick", "Electric", "Gentle", "Sharp", "Flowing",
            "Laid-back", "Silky", "Quiet", "Uptown", "Classy", "Dynamic", "Groovy", "Shining", "Swaying", "Funky",
            "Blazing", "Bright", "Sophisticated", "Whispering", "Nightly", "Smoky", "Crisp", "Satin", "Fluid", "Resonant",
            "Warm", "Jazzy", "Graceful", "Bold", "Free", "Easy", "Dreamy", "Echoing", "Swinging", "Vibrant"],
          nouns: ["Swing", "Trio", "Quartet", "Swingers", "Rhythm", "Vibe", "Groove", "Harmony", "Blues", "Breeze",
            "Night", "Soul", "Bass",
            "Horn", "Chord", "Melody", "Tone", "Beat", "Session", "Syncopation", "Jam", "Bassline", "Sax",
            "Trumpet", "Quartet", "Sextet", "Note", "Cadence", "Fusion", "Improv", "Keys", "Quartet", "Octave",
            "Bridge", "Lounge", "Club", "Moonlight", "Sizzle", "Snare", "Shuffle", "Bebop", "Riff", "Midnight",
            "Rhythm", "Brushes", "Stomp", "Break", "Solo", "Chord", "Bop", "Pulse", "Groove", "Reverb"]

        },

        pop: {
          adjectives: ["Ganja", "Jah", "Conscious", "Sonic", "Rasta", "", "Cosmic", "Mega", "Super", "Giant",
            "Sonic", "Bill Marley",],
          nouns: ["Rockers", "Drifters", "Jam", "Vortex", "Living", "Pulse", "Rebels", "and the Wafflers",
            "Quest", "Specter", "Cloud Formation", "Ark", "Nebula", "Oracle", "and the Eclipse", "Sandwich"],
          wildcards: ["Utterly Wednesday", "What Happened in Vegas", "Exasperated Footwork", "Untainted Journalism"]

        },

        punk: {

          adjectives: ["Violent", "Brutal", "Defiant", "Savage", "Hostile", "Furious", "Raw", "Reckless", "Toxic", "Noisy",
            "Rebellious", "Doomed", "Outraged", "Broken", "Angry", "Relentless", "Raging", "Unruly", "Ruthless", "Underground",
            "Untamed", "Wild", "Crazed", "Unstoppable", "Reckless", "Destructive", "Gritty", "Explosive",
            "Dysfunctional", "Anti", "Anarchic", "Chaotic", "Torn", "Bitter", "Harsh", "Vicious", "Distorted",
            "Scarred", "Unforgiving", "Corrupt", "Loud", "Dirty", "Ugly", "Sharp", "Aggressive", "Reckless", "Fearless", "Radical", "Reckless", "Defiant"],

          nouns: ["Revolt", "Chaos", "Anarchy", "Rebellion", "Youth", "Crash", "Fury", "Vandal", "Scream", "Disaster",
            "Riot", "Crisis", "Rejection", "Outcast", "Threat", "Sabotage", "Misfit", "Mutiny", "Disorder", "Havoc",
            "Blitz", "Dissent", "Reckoning", "Venom", "Rebellion", "Wreck", "Resistance", "Grind", "Barricade", "Rubble",
            "Snarl", "Fist", "Vendetta", "Mayhem", "Outrage", "Burn", "Distortion", "Grudge", "Shrapnel", "Whiplash",
            "Scum", "Insurgency", "Parasite", "Inferno", "Brawl", "Backlash", "Trigger", "Razor", "Outbreak", "Wasteland"]

        },

        reggae: {
          adjectives: ["Ganja", "Jah", "Conscious", "Sonic", "Rasta", "Cosmic", "Mega", "Super", "Giant", "Sonic", "Bill Marley",],
          nouns: ["Rockers", "Drifters", "Jam", "Living", "Pulse", "Rebels", "Quest", "Specter", "Cloud Formation", "Ark", "Nebula", "Oracle", "and the Eclipse", "Sandwich"],
          wildcards: ["Jamtastic and the Wafflers", "Jah Rebels"]
        },

        rock: {
          adjectives: ["Blistering", "Iron", "Venomous", "Burnt", "Steel", "Mystic", "Furious", "Deadly", "Wicked", "Fallen", "Glorious", "Shadowed", "Broken", "Black", "Frozen", "Reckless", "Fiery", "Crushing", "Unchained", "Vicious", "Distant", "Eternal", "Twisted", "Savage", "Bleeding", "Rebel", "Chaos", "Beast", "Dragon", "Nightmare", "Bullet", "Fury", "Breaker", "Horizon", "Serpent", "Blade", "Eclipse", "Ghost", "Hunter", "Thunderbolt", "Machine", "Banshee", "Falcon", "Glory", "Mercenary", "Scorpion", "Blaze", "Talon", "Rocket", "Outlaw", "Viper", "Inferno", "Shadow", "Jaguar", "Vanguard", "Bullet", "Tsunami", "Wolves", "Storm", "Vortex", "Titan", "Iron", "Dagger", "Flame", "Cobra", "Echo", "Thunder", "Balls of", "Sonic", "Electric", "Atomic", "Cosmic", "Mega", "Super", "Giant", "Sonic"],
          nouns: ["Rockers", "Drifters", "Fury", "Glory", "Machine", "Vortex", "Pulse",
            "and the Quasar", "Quasar", "Crimson", "Atomic", "Burning", "Wild", "Feral", "Silver", "Neon", "Electric", "Crimson", "Atomic", "Burning",
            "Wild", "Feral", "Silver", "Neon", "Savage", "Lunar", "Shattered", "Scarlet", "Blazing", "Golden",
            "Dark", "Furious", "Venomous",],
          wildcards: ["Balls of Fury", "Mars Amnesia", "Shmucks on Wheels", "Unbeatable Candor", "Blistering Sandwich",
            "Uncomfortable Machine", "Gaping Chasm", "That Really Escalated"]

        }

      }

    };
  },

  methods: {
    generateName() {
      const genreData = this.genres[this.selectedGenre];

      // Randomly decide whether to use 'adj noun' or 'wildcard'
      const useWildcard = Math.random() < 0.2;

      if (useWildcard && genreData.wildcards) {
        // Pick a random wildcard
        const wildcard = genreData.wildcards[Math.floor(Math.random() * genreData.wildcards.length)];
        this.generatedName = wildcard;
      } else {
        // Pick a random adjective and noun
        const adj = genreData.adjectives[Math.floor(Math.random() * genreData.adjectives.length)];
        const noun = genreData.nouns[Math.floor(Math.random() * genreData.nouns.length)];
        this.generatedName = `${adj} ${noun}`;
      }
    }
  }
};

</script>

<style scoped>
h1 {
  color: white;
  font-size: 8rem;
  font-family: Impact, Haettenschweiler, 'Arial Narrow Bold', sans-serif;
  margin-bottom: 0px;
  text-shadow: 4px 2px 4px #afa9a9;
}

h2 {
  color: white;
  font-family: Impact, Haettenschweiler, 'Arial Narrow Bold', sans-serif;
  font-style: oblique;
}


button {
  background-color: white;
  width: 18rem;
  height: 4rem;
  border-radius: 7px;
  font-family: Arial, Helvetica, sans-serif;
  font-weight: bold;
  font-size: 18px;
  margin-top: 100px;
  box-shadow: 2px 2px 3px rgb(63, 62, 62);
  color: rgb(196, 27, 27);
}

button:hover {
  color: rgb(196, 27, 27);
  text-decoration: none;
  background-color: rgb(154, 154, 154);
}

#band-name-display {
  background-color: white;
  width: 30rem;
  height: 3rem;
  border-radius: 5px;
  margin-top: 35px;
  font-family: Arial, Helvetica, sans-serif;
  font-size: 18px;
  font-weight: bold;
  text-align: center;
  margin-bottom: 300px;
}

.amp-knob {
  margin-top: 0px;
  font-family: Arial, Helvetica, sans-serif;
  font-size: 18px;
  /* background-image: radial-gradient(circle, #777, #555); */
  background-color: rgb(154, 154, 154);
  border: 5px solid #313030;
  box-shadow:
    /* inset 0px 5px 10px rgba(0, 0, 0, 0.6), Inner shadow for depth */
    7px 7px 9px 1px rgba(3, 3, 3, 0.5);
  width: 10rem;
  height: 10rem;
  border-radius: 50%;
  display: flex;
  flex-direction: column;
  justify-content: center;
  color: white;
  margin-top: 5px;
  margin-bottom: 5px;
  margin-left: 15px;

}

.home {
  display: flex;
  flex-direction: column;
  align-items: center;
}


#select-genre {
  font-size: 19px;
  font-weight: medium;
  margin-bottom: 10px;
  color: white;
  font-family: Arial, Helvetica, sans-serif;
  font-weight: bold;
}

#select-words {

  font-size: 19px;
  font-weight: medium;
  margin-bottom: 10px;
  color: white;
  font-family: Arial, Helvetica, sans-serif;
  font-weight: bold;
}


#select-spicy {
  font-size: 17px;
  font-weight: medium;
  margin-bottom: 10px;
  color: white;
  font-family: Arial, Helvetica, sans-serif;
  font-weight: bold;
}

.control-panel {
  /* background-color: rgb(214, 201, 199); */
  width: 40%;
  height: 150px;
  border-radius: 10px;
  margin-top: 75px;
  display: flex;
  flex-direction: row;
  justify-content: space-evenly;
  align-items: center;
  /* border: 9px solid #201f1f; */
  /* background-image: radial-gradient(circle, #777, #555); */
  /* background-image: url('@/assets/Black.jpg'); */
}


.make-dropdown {

  font-family: Arial, Helvetica, sans-serif;
  font-size: 16px;


}
</style>

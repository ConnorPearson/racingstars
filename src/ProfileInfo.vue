<template>
  <div id = "app">
    <main>
      <div class="container">

        <div class="image"></div>

        <h3>Birthday Calculator</h3>

        <p>Please enter your birthday below and click 'Get Birthday Stats' to calculate the days since you were born and the days until your next birthday!</p>

        <table>
          <tr>
            <th>
              <label for="birthday">Date of Birth : </label>
            </th>

            <th>   
              <input type="date" id="birthday" name="birthday" v-model="birthday" required>
            </th>
          </tr>
        </table>

        <div id = "statsContainer">

          <table>
            <tr>
              <th>
                <label id="statsLabel">Days since birth : </label>
              </th>

              <th>   
                <label id="statsAccentLabel">{{daysSinceBirthdate}}</label>
              </th>
            </tr>

            <tr>
              <th>
                <label id="statsLabel">Days until birthday : </label>
              </th>

              <th>   
                <label id="statsAccentLabel">{{daysUntilBirthday}}</label>
              </th>
            </tr>
          </table>

        </div>
        
        <button id = "birthdayStatsBtn" v-on:click="getBirthdayStats()">Get Birthday Stats</button>  


      </div>
    </main>
  </div>
</template>

<script>
  export default {
    name: 'ProfileInfo',

    data() {
      return {
        birthday : "",
        daysUntilBirthday : "--",
        daysSinceBirthdate : "--"
      }
    },

    methods: {
      getBirthdayStats() {
        let currentDate = new Date();
        let birthdate = new Date(this.birthday);
        let nextBirthday = new Date(birthdate.valueOf());

        // Ensure a valid date is entered, if not exit script
        if ( !(birthdate instanceof Date && !isNaN(birthdate)) ) {
          console.log("Invalid date value provided.")

          alert("Invalid date value provided.")
          
          return 0;
        }

        // Ensure the provided date is in the past.
        if (currentDate.getTime() < birthdate.getTime()){
          console.log("Given birthdate has not yet happened.");

          alert("Given birthdate has not yet happened.")

          return 0;
        }

        // Create a copy of the birthday object with current year as year value
        nextBirthday.setFullYear(currentDate.getFullYear());

        // Check projected next birthday has not already passed, if so increment year
        if (currentDate.getTime() > nextBirthday.getTime()) {
          nextBirthday.setFullYear(nextBirthday.getFullYear() + 1);
        }

        // Calculate difference between dates in miliseconds and divide by milliseconds in a day. Round down for display purposes.
        this.daysUntilBirthday = Math.floor((nextBirthday.getTime() - currentDate.getTime()) / (1000 * 60 * 60 * 24));
        this.daysSinceBirthdate = Math.floor((currentDate.getTime() - birthdate.getTime()) / (1000 * 60 * 60 * 24));

        if (this.daysUntilBirthday === 364) {
          alert("🥳 Happy Birthday! 🥳")
        }
      }
    }
  }

</script>

<style>

  * {
    margin : 0;
    padding: 0;
  }

  html {
    margin : 0;
  }

  h3 {
    font-family: 'Avenir', 'Inter var',ui-sans-serif,system-ui,-apple-system,BlinkMacSystemFont,Segoe UI,Roboto,Helvetica Neue,Arial,Noto Sans,sans-serif,Apple Color Emoji,Segoe UI Emoji,Segoe UI Symbol,Noto Color Emoji;
    font-size: 2.25rem;
    line-height: 2.5rem;
    letter-spacing: -.025em;
    font-weight: 800;
    
    margin-bottom: 5%;
    
    color: #FFFFFF;    
  }

  .container {
    background-color : #343c4f;
    color : #d8dee9;

    padding: 15px;
    margin: 0px auto;

    border-radius: 10px;
    border-style: solid;
    border-width: 0px;

    width : 640px;
    height: 450px;

    justify-content : center;

    box-shadow: 1px 1px 1px rgb(22, 18, 48), 0 0 10px #2b313c, 0 0 1px rgb(0, 0, 0);
  }

  table {
    margin : auto;
  }

  #birthday {
    padding: 0px;
    margin: 0px;

    width: 100%;
    height: 100%;

    color: rgb(43, 49, 60);;
    background-color: #d8dee9; 
    border-color: #d2d2d2;

    border-radius: 5px;
    border-style: solid;
    border-width: 3px;

    font-size: normal;

    height : 28px;
    width : 160px;
  }

  button {
    color: #d8dee9;
    background-color: #2b313c;
    border-color: #00739d;

    border-radius: 5px;
    border-style: solid;
    border-width: 3px;

    font-size: normal;

    height : 40px;
    width : 160px;

    position: relative;
    top: 20px;

    transition-duration: 0.2s;
  } 

  button:hover {
    background-color: #00739d;
    color: white;
  }

  th{
    padding: 5px;
  }


  #app {
    background-image: url('./assets/backdrop.jpg');
    background-size: cover;
    background-position: bottom;

    margin-top : 0px;
  }

  main {
    min-height : 100vh;
    padding : 25px;

    height : auto;
  }

  p {
    margin-bottom: 20px;
  }

  #statsLabel {
    display: table-cell;
    text-align: right;


    width : 200px;
  }

  #statsAccentLabel {
    display: table-cell;
    text-align: left;

    color: #00739d;

    width: 200px;
  }

  #statsContainer {
    border-color: #00739d;

    border-radius: 5px;
    border-style: solid;
    border-width: 3px;

    margin: 30px;
  }

</style>
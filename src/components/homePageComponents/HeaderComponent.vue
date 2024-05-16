<template>
      <Header id="header-component-container">
        <div id="header-contents-container">
          <h1>Book Marker</h1>
          <div id="header-searchContainer">
            <input type="text" placeholder="Search Books">
              <a href="">
                <li class="fas">Search</li>
              </a>
          </div>
        </div>
      </Header>
</template>
  
  <script>

  </script>

 
<style scoped>
  @import url('~@fortawesome/fontawesome-free/css/all.css');

  /* Adjustments for mobile */
  @media screen and (min-width: 320px) {
    #header-contents-container {
      background-color: var(--primary-colour);
      padding: 10px;
      flex-direction: column;
      align-items: flex-start;
      height: 15vh;
      color: white;
    }

    #header-searchContainer {
      margin: 10px auto;
      background: #fff;
      height: 30px;
      border-radius: 30px;
      padding: 10px 20px;
      display: flex;
      align-items: center;
      transition: 0.8s;
      box-shadow: 0 0 25px 0 rgba(0, 0, 0, 0.4);
    }

    #header-searchContainer:hover input {
      width: 350px;
    }

    #header-searchContainer input {
      background: transparent;
      border: none;
      outline: none;
      width: 0px;
      font-weight: 500;
      font-size: 16px;
      transition: 0.8s;
    }

    #header-searchContainer li .fas {
      color: var(--secondary-colour);
    }

    .header-right {
      float: none; /* Reset float */
      width: 100%; /* Take full width */
      text-align: left; /* Align text left */
    }
  }

  /* Additional styles go here */
</style>

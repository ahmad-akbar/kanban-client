<template>
  <!-- NAVBAR  -->
  <div>
    <nav class="navbar navbar-expand-lg navbar-light bg-light shadow" >
      <div class="container-fluid">
        <a class="navbar-brand" href="#">Kanban</a>
        <!-- <img src="data:image/png;base64,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"  alt="" width="30" height="24"> -->
          <div class="collapse navbar-collapse" id="navbarSupportedContent">
          <ul class="navbar-nav me-auto mb-2 mb-lg-0">
              <li class="nav-item" v-if="dataIsLogin">
              <a class="btn btn-outline-danger" aria-current="page" href="#" @click="btnLogout">Logout</a>
            </li> 
            <li class="nav-item" v-if="dataIsLogin">
              <a class="btn btn-outline-info" aria-current="page" href="#" >Add Task</a>
            </li>            
        </div>
      </div>
    </nav>
  </div>
</template> 

<script>
export default {
    props:['dataIsLogin','btnLogout']
};
</script>

<style>
body {
    background: #eee
}

.header2 {
    font-family: "Montserrat", sans-serif;
    color: #8d97ad;
    font-weight: 300
}

.header2.bg-success-gradiant {
    background: #2cdd9b;
    background: -webkit-linear-gradient(legacy-direction(to right), #2cdd9b 0%, #1dc8cc 100%);
    background: -webkit-gradient(linear, left top, right top, from(#2cdd9b), to(#1dc8cc));
    background: -webkit-linear-gradient(left, #2cdd9b 0%, #1dc8cc 100%);
    background: -o-linear-gradient(left, #2cdd9b 0%, #1dc8cc 100%);
    background: linear-gradient(to right, #2cdd9b 0%, #1dc8cc 100%)
}

.header2 .font-12 {
    font-size: 12px
}

.header2 .dropdown-item {
    padding: 8px 1rem;
    color: #8d97ad
}

.header2 .h2-nav .navbar-nav .nav-item .nav-link {
    padding: 12px 0px;
    color: #ffffff;
    font-weight: 400
}

.header2 .h2-nav .navbar-nav .nav-item .nav-link:hover {
    color: #263238
}

.header2 .h2-nav .navbar-nav .nav-item {
    margin: 0 20px
}

@media (min-width: 1024px) {
    .header2 .navbar-nav>.dropdown .dropdown-menu {
        min-width: 210px;
        margin-top: 0px
    }
}

@media (min-width: 1024px) {
    .header2 .dropdown-submenu:hover>.dropdown-menu {
        display: block
    }
}

.header2 .dropdown-toggle::after {
    display: none
}

@media (min-width: 1024px) {
    .header2 .hover-dropdown .navbar-nav>.dropdown:hover>.dropdown-menu {
        display: block;
        margin-top: 0px
    }
}

.header2 .btn-dark {
    color: #fff;
    background-color: #343a40;
    border-color: #343a40
}

.header2 .btn-dark:hover {
    color: #fff;
    background-color: #23272b;
    border-color: #1d2124
}

.header2 .h2-nav .navbar-nav .nav-item .btn {
    opacity: 0.5
}

.header2 .h2-nav .navbar-nav .nav-item .btn:hover {
    opacity: 1
}

.header2 .dropdown-submenu>.dropdown-menu {
    top: 0;
    left: 100%;
    margin-left: 0;
    border-radius: 0.25rem;
    display: none
}
</style>
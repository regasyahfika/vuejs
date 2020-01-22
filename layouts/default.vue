<template>
  <div>
    <b-navbar toggleable="lg" type="dark" variant="info">
      <b-navbar-brand to="/">Home</b-navbar-brand>

      <b-navbar-toggle target="nav-collapse" />

      <b-collapse id="nav-collapse" is-nav>
        <b-navbar-nav>
          <b-nav-item to="/todolist">ToDoList</b-nav-item>
        </b-navbar-nav>
      </b-collapse>
    </b-navbar>
    <b-container>
      <nuxt />
    </b-container>
  </div>
</template>

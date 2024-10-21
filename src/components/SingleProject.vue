<template>
  <div class="project">
    <div class="flexing">
      <div>
        <h3 @click="showDetail = !showDetail">{{ project.title }}</h3>
      </div>  
      <div>
        <span class="material-icons">delete</span>
        <span class="material-icons">edit</span>
        <span class="material-icons">done</span>
      </div>
    </div>
    <p v-if="showDetail">{{ project.detail }}</p>
  </div>
</template>

<script>
export default {
  props: ['project'],
  data() {
    return {
      showDetail: false
    }
  }
}
</script>

<style>
.project {
  width: 100%;
  padding: 20px;
  background-color: #f2f2f2;
  cursor: pointer;
  margin: 10px;
  border-left: 5px solid crimson;
  border-radius: 8px;
}

h3 {
  color: indigo;
}

p {
  color: #2c3e50;
}

.flexing {
  display: flex;
  justify-content: space-between;
  align-items: center;
}

span {
  margin-left: 10px;
}

span:hover {
  color: #777;
}
</style>
<script setup>
  import {ref} from 'vue'
  const tags = ref(['coding', 'javascript', 'html', 'css', 'php', 'nodejs', 'python']);
  const newTag = ref('');
  const maxTags =  10;

  // them tag
  const addTags = () => {
    const tag = newTag.value.trim();
    if(tag && !tags.value.includes(tag)){
      tags.value.push(tag)
    }
    newTag.value="";
  }

  // xoa 1 tag
  const removeTag = (index) => {
    tags.value.splice(index,1)
  }

  // xoa tat ca tag
  const removeAll = () => {
    tags.value = [];
  }
</script>
<template>
  <div>
    <h3>Tags</h3>
    <p>Press enter or add a comma after each tag</p>
    <div class="tags-container">
      <span v-for="(tag,index) in tags ":key = index class="tag">
        {{ tag }}
        <button @click="removeTag(index)">x</button>
      </span>
      <input 
        v-if="tags.length < maxTags"
        type="text"
        v-model="newTag"
        @keyup.enter="addTags"
        @keyup=";"
        placeholder="Enter tag..."
      >
    </div>
    <div class=""inline-container>
      <p>{{ maxTags - tags.length }}tags are remaining</p>
      <button @click="removeAll">Remove all</button>
  </div>
  </div>
</template>
<style scoped>
  .tags-container{
    display: flex;
    flex-wrap: wrap;
    gap: 10px;
    padding: 10px;
    border: 1px solid #ccc;
    border-radius: 5px;
  }
  .tag{
    display: inline-flex;
    align-items: center;
    background-color: #f0f0f0;
    padding: 5px 10px;
    border-radius: 5px;
  }
  .tag button{
    background: none;
    border: none;
    margin-left: 5px;
    cursor: pointer;
    color: red;
  }
  input {
  border: none;
  padding: 5px;
  outline: none;
}

button {
  margin-top: 10px;
  padding: 5px 10px;
  background-color: #5171f0;
  color: white;
  border: none;
  cursor: pointer;
}

button:hover {
  background-color: #45a049;
}
.inline-container {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-top: 10px;
}

.inline-container p {
  margin: 0;
}

.inline-container button {
  margin-left: 10px;
}
</style>
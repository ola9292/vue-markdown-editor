<script setup>
import { ref, computed, shallowReactive } from 'vue';
import { marked } from "marked";

const rawtext = ref('# hello')
const markdownText = computed(() => {
        return marked(rawtext.value);
})

</script>

<template>
        <div class="container">
                <h2 class="text-center">Markdown Editor</h2>
                <div class="whole">
                        <div class="preview editor">
                                <div class="toolbar">
                                        <span><strong>Editor</strong></span>
                                        <span @click="toggleEditor"><i class="fa-solid fa-xmark"></i></span>
                                </div>
                                <textarea v-model="rawtext"  placeholder="Type your Markdown here..."></textarea>
                        </div>
                        
                        <div class="preview previewer">
                                <div class="toolbar">
                                        <span><strong>Previewer</strong></span>
                                        <span><i class="fa-solid fa-xmark"></i></span>
                                </div>
                                <div v-html="markdownText" class="preview-area"></div>
                        </div>
                        
                </div>
        </div>  
        
</template>

<style scoped>
.text-center{
        text-align: center;
}
.container{
        /* border: 1px solid red; */
        width: 100%;
}
.whole{
        display: grid;
        gap: 30px;
        width: 100%;
}
.text{
        width: 700px;
        margin: auto;
}
.preview{
     display: flex;
     flex-direction: column;
     box-shadow: rgba(0, 0, 0, 0.35) 0px 5px 15px;
}
.editor{
        width: 600px;
        margin: auto;
}
.previewer{
        width: 900px;
        margin: auto;  
}
.toolbar{
        padding: 4px 20px;
        display: flex;
        justify-content: space-between;
        background-color: #4aa3a3;
}
textarea{
  width: 100%;
  height: 100%;
  border: none; 
  outline: none;
  resize: none;
  font-size: 1rem;
  padding: 1rem;
  box-sizing: border-box; 
  background-color: #c0d8d8;
}
.preview-area{
        background-color: #c0d8d8;
        padding: 8px 20px;
}
@media (max-width: 768px) {
    .whole {
        grid-template-columns: 1fr; /* Stack editor and previewer vertically */
        gap: 20px;
    }

    .editor, .previewer {
        width: 100%; /* Make them take full width of the container */
        max-width: 100%; /* Remove the 90% limitation for smaller screens */
    }

    textarea {
        height: 200px; /* Adjust height for smaller screens */
    }
}
</style>
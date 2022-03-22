<template>
<div>
    <h1>miniPad</h1>
    <h2>
        <button @click.prevent="change_title" class="title_b">{{title}}</button> <br>
        <label class="title_hint">Press on the title to change it.</label>
    </h2>
    <textarea rows="25" class="text_editor" placeholder="Enter text here..." v-model="content"></textarea>
    <button @click.prevent="save_file" class="save_b">Save</button>
</div>
</template>

<script>
import saveAs from 'file-saver'

export default {
    data() {
        return {
            title: 'New File',
            content: '',
        }
    },

    methods: {
        change_title() {
            this.backTitle = this.title
            this.title = prompt('Enter new title:')
            if(this.title == null || this.title.replace(/\s+/g, '') == '') {
                this.title = this.backTitle
            }
        },
        
        save_file() {
            if(this.content.replace(/\s+/g, '') != '') {
                var blob = new Blob([this.content], {type: "text/plain;charset=utf-8"})
                this.file_name = prompt("Enter file name:", this.title + ".txt")
                if(this.file_name.replace(/\s+/g, '') != '')
                    saveAs(blob, this.file_name)
            }
        }
    }
}
</script>

<style>
.text_editor {
    width: 100%;
    background-color: #131313;
    color: #ffffff;
    border: none;
    border-radius: 5px;
    margin-top: 5px;
    white-space: pre-wrap;
}
.title_b {
    background-color: #181818;
    color: #ffffff;
    border: none;
    padding: 0px;
    font-size: 150%;
    cursor: pointer;    
}
.save_b {
    background-color: #101010;
    color: #ffffff;
    border: none;
    padding: 10px;
    border-radius: 5px;
    margin-top: 5px;
    margin-bottom: 5px;
    font-size: 150%;
    cursor: pointer;
    width: 200px;
}
.title_hint {
    opacity: 50%;
    font-size: 75%;
    font-weight: normal;
}
</style>
<template >
    <div class="todo-section">
        <div class='todo-panel'>
                 
                <div class="todo__name">Notes</div>               
                    
                <div  class="todo__box" >
                <h3 v-on:click="indexChanger">
                    {{buttonOpenName[index]}}
                </h3>
                     
                  <input type="text" 
                  v-model="inputName" 
                  class="name-input" 
                  v-if="openInput"
                  placeholder="Title"
                  >
                    <textarea maxlength="195"  
                    class="new-todo" 
                    v-model="inputValue" 
                    v-if="openInput"
                    placeholder="Text"
                    >
                        
                        
                    </textarea>
                    <button class="input-btn" v-on:click="inputEnter"   v-if="openInput&!noteIsOpen">add note</button>
                    <button class="input-btn edit-btn" @click="enterEdit" v-if="noteIsOpen">edit</button>
                </div>
    
                
                
                <div class="note-bar">
                    <div class="note-item"  
                    v-if="openInput===false"  
                    v-for="(note,i) of notes"
                    @click="openNote(i)"
                    >
                    <div class="number-of-note">{{i+1}}.</div>
                    <div class="close-btn" v-on:click.stop="noteDelete(i)">x</div>
                    {{note.name}}
                    
                    </div>
                </div>
                
                
                    
                    
                   
                
                    
                        
                    
               
                   
           </div>
    </div>
</template>
<script>
export default {
     data() {
        return{
            
            notes: [],
            nameNote: '',
            inputValue: '',
            inputName: '',
            openInput: false,
            buttonOpenName: ['+','back'],
            index: 0,
            noteIsOpen: false,
            textAdd: '',
            notesI: 0

            
            
            
            
            
        } 
    },
    methods: {

        inputEnter (){
           let objNote = {name:this.inputName, text:this.inputValue}
           this.notes.push(objNote)
           this.index--;
           this.openInput=false;
           this.inputValue = '';
           this.inputName = ''
           this.noteIsOpen = false
        },
        indexChanger (){
            if (this.openInput) {this.openInput=false; this.index=0} else {this.openInput=true; this.index=1}
            if (this.noteIsOpen) {this.noteIsOpen=false} 
            
 
         },
        noteDelete(i) {
             this.notes.splice(i,1); 
        },
        openNote(i){
             this.openInput = true
             this.noteIsOpen = true
             this.inputValue = this.notes[i].text
             this.inputName = this.notes[i].name
             this.index = 1
             this.notesI = i


            

        },
        enterEdit(){
           this.notes[this.notesI].text= this.inputValue
           this.notes[this.notesI].name=this.inputName 
            this.indexChanger()
        }
        
    
}
}
</script>
<style scoped>
    * {
    vertical-align: baseline;
    font-weight: inherit;
    font-family: inherit;
    font-style: inherit;
    font-size: 100%;
    border: 0 none;
    outline: 0;
    padding: 0;
    margin: 0;
    -webkit-box-sizing: border-box;
            box-sizing: border-box;
    font-family: "Oswald", sans-serif;

  }
 
.todo-section {
    background-color: rgb(177, 241, 180);
    padding: 100px 0;
    max-width: 1920px;
    margin: 0 auto;
}
.todo-panel {
    height: 628px;
    width: 400px;
    margin: 0 auto;
    background-color: rgb(204, 208, 181);
    padding-top: 10px;
    position: relative;
    border-radius: 20px;
    margin-top: 40px;
    padding: 25px;
    color: black;
    border: 1px solid black;
    
}
.todo__box{
    background-color: rgb(234, 251, 124);
    
    margin: 0 auto;
    
    text-align: center;
    cursor: pointer;
    transition: 0.1s;
    display: block;
    margin-bottom: 10px;
    text-decoration: none;
    color: black;
    box-shadow: 0 0 10px 0.1px black;
   
    
}
.todo__box h3 {
   
    border-bottom: 1px solid black;
   font-size: 25px;
    padding: 10px;
    font-weight: 100;
    display: block;
    color: black;
    
    
    
}

.todo__name {
    text-align: center;
    font-size: 20px;
    font-weight: 200;
    margin-bottom: 10px;
    color: black;
}
.popup-close {
   margin-bottom: 20px;
   display: block;
}

.input-btn {
    
    border: 2px solid black;
    color: black;
    margin: 0 auto;
    cursor: pointer;
    width: 100px;
    border-radius: 10px;
    padding: 10px;
    text-align: center;
    margin-bottom: 10px;
    
}
.input-btn:hover {
    filter: brightness(1.05);
}

.name-input {
    width: 70%;
    border-bottom: 1px solid black;
    background-color: rgb(234, 251, 124);
    height: 50px;
    color: black;
    font-size: 40px;
    font-family: 'Caveat';
    text-align: center;
    
}

.new-todo {
   
    display: block;
    font-family: 'Caveat';
    resize: none;
    color: black;
    padding: 10px;
    height: 300px;
    border-radius: 20px; 
    background-color: rgb(234, 251, 124);
    width: 100%;
    margin-bottom: 30px;
    font-size: 30px;
    
  
    
}
.close-btn {
    position: absolute;
    width: 30px;
    height: 30px;
    color: black;
    top: 0;
    right: 0;
    font-size: 20px;
    justify-content: center;
    display: flex;
    align-items: center;
    border-left: 1px solid black;
    border-bottom: 1px solid black;
}
.close-btn:hover {
    font-size: 15px;
    
    
    

}
.note-item {
    display: flex;
    width: 150px;
    height: 150px;
    background-color: rgb(234, 251, 124);
    color: black;
    justify-content: center;
    align-items: center;
    cursor: pointer;
    transition: 0.1s;
    margin-bottom: 10px;
    text-decoration: underline;
    position: relative;
    
}
.note-item:hover {
    
    box-shadow: 0 0 5px 1px black;
    
}


.note-bar {
    display: grid;
    grid-template-columns: 1fr 1fr;
    justify-items: center;
    overflow-y: scroll;
    overflow-x: hidden;
    max-height: 449px;
    align-items: start;
}
.absolute-input {
    position: absolute;
    z-index: 500000;
}
.number-of-note {
    position: absolute;
    top: 5px;
    left: 5px;
}


.note-bar::-webkit-scrollbar {
    width: 3px;  
     height: 100px;           /* ширина scrollbar */
  }
  
  .note-bar::-webkit-scrollbar-thumb {
    background-color: rgb(114, 114, 114);    /* цвет плашки */
    border-radius: 20px; 
         /* закругления плашки */
     /* padding вокруг плашки */
  }
  body::-webkit-scrollbar {
    display: none;         /* ширина scrollbar */
  }

</style>
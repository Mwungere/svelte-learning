<script>
    import {createEventDispatcher} from 'svelte' 
   import Button from "../shared/Button.svelte";
   let fields = { question: "", answerA: "", answerB: "" };
   let errors = { question: "", answerA: "", answerB: "" };
   let valid = false;
 
   let dispatch = createEventDispatcher();
 
   const submitHandler = () => {
     valid = true;
     //validate question
 
     if (fields.question.trim().length < 5) {
       valid = false;
       errors.question = "Question must be at least 5 characters";
     } else {
       errors.question = "";
     }
 
     //validate answer A
 
     if (fields.answerA.trim().length < 1) {
       valid = false;
       errors.answerA = "Answer must be at least 1 characters";
     } else {
       errors.answerA = "";
     }
 
     //validate answer B
     if (fields.answerB.trim().length < 1) {
       valid = false;
       errors.answerB = "Answer must be at least 1 characters";
     } else {
       errors.answerB = "";
     }
 
     //add new poll
 
     if (valid) {
         let poll = {...fields, votesA: 0, votesB: 0, id: Math.random()};
         dispatch('add', poll);
     }
   };
 </script>
 
 <form on:submit|preventDefault={submitHandler}>
   <div class="form-field">
     <label for="question">Poll Question:</label>
     <input type="text" id="question" bind:value={fields.question} />
     <div class="errors">{errors.question}</div>
   </div>
   <div class="form-field">
     <label for="answer-a">Answer A:</label>
     <input type="text" id="answer-a" bind:value={fields.answerA} />
     <div class="errors">{errors.answerA}</div>
   </div>
   <div class="form-field">
     <label for="answer-b">Answer B:</label>
     <input type="text" id="answer-b" bind:value={fields.answerB} />
     <div class="errors">{errors.answerB}</div>
   </div>
   <Button type="secondary" flat={true}>Add Poll</Button>
 </form>
 
 <style>
   form {
     width: 400px;
     margin: 0 auto;
     text-align: center;
   }
   .form-field {
     margin: 18px auto;
   }
   input {
     width: 100%;
     border-radius: 6px;
   }
   input:focus {
     outline: 2px solid #45c496;
   }
 
   label {
     margin: 10px auto;
     text-align: left;
   }
 
   .errors {
     font-weight: bold;
     font-size: 11px;
     color: #d91b42;
   }
 </style>
 
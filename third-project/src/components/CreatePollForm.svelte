<script>
    import {createEventDispatcher} from '../../../first-project/node_modules/svelte/types/runtime';
    import Button from "../shared/Button.svelte";

    let dispatch = createEventDispatcher(); //Dispatch func
    let fields ={
        question:'',
        answerA:'',
        answerB:''
    }
    let errors = {
        question:'',
        answerA:'',
        answerB:''
    }
    let valid = false;
    const submitHandler = (e)=>{
        valid=true;

        //validate question
        if(fields.question.trim().length < 5){
            valid = false;
            errors.question = 'question must be at least 5 chars'
        }else{
            errors.question = ''
        }

        //validate answer A
        if(fields.answerA.trim().length < 1){
            valid = false;
            errors.answerA = 'Answer must be at least 5 chars'
        }else{
            errors.answerA = ''
        }
        //Add a new poll
        if(valid){
            console.log(`valid ${fields}`)
        }

        //validate answer B
        if(fields.answerB.trim().length < 2){
            valid = false;
            errors.answerB = 'Answer must be at least 5 chars'
        }else{
            errors.answerB = ''
        }
        //Add new poll
        if(valid){
          let poll = {...fields, votesA:0, votesB:0, id: Math.random()*100}
          dispatch('add',poll);
          console.log()  
        }
    }
</script>

<form on:submit|preventDefault={submitHandler}>
   <div class="form-field">
        <label for="question">Poll Question:</label>
        <input type="text" id="question" bind:value={fields.question}>
    <div class="error">{errors.question}</div>
   </div>

   <div class="form-field">
        <label for="answer-a">Answer A:</label>
        <input type="text" id="answer-a" bind:value={fields.answerA}>
        <div class="error">{errors.answerA}</div>
   </div>

   <div class="form-field">
        <label for="answer-b">Answer B</label>
        <input type="text" id="answer-b" bind:value={fields.answerB}>
        <div class="error">{errors.answerB}</div>
   </div>
   <Button
    type="secondary"
    flat={"true"}
    inverse={false}
   >Add Poll </Button>
</form>

<style>
    *{
        box-sizing: border-box;
        margin:0;
        padding:0;
    }
    form{
        width:400px;
        margin: 0 auto;
        text-align: center;
    }
    .form-field{
        margin: 18px auto;
        font-size:20px;
    }
    input{
        width:100%;
        border-radius:6px;
    }
    label{
        margin:10px auto;
        text-align:left;
    }
    .error{
        font-weight:bold;
        font-size:12px;
        color:crimson;

    }
</style>
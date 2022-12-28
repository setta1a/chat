<template>
  <div id="app">
    <Container>
      <ChatWindow @sendMessageEvent="sendMessageData($event)">
        <ChatMessage v-for="message in messages" 
        :key="message.id" 
        :username="message.author" 
        :time="message.datetime">
        {{ message.text }}
        </ChatMessage>
      </ChatWindow>
    </Container>
  </div>
</template>

<script>
  import Container from './components/Container.vue'
  import ChatMessage from './components/ChatMessage.vue'
  import ChatWindow from './components/ChatWindow.vue'
  export default {
    name: 'App',
    components: {
      Container,
      ChatMessage,
      ChatWindow
    },
    data(){
      return {
        messages: []
      }
    },
    methods:{
      getMessagerData(){
        this.axios.get('https://61bcd385d8542f0017824a2a.mockapi.io/messages')
          .then((response)=>{
            this.messages = response.data
            console.log(this.messages)
          })
      },
      sendMessageData(data){
        this.axios( {
            method: 'post',
            url: "https://61bcd385d8542f0017824a2a.mockapi.io/messages",
            data: {
                author: data.username,
                text: data.messageText
            }
        }).then((response) => {
            console.log(response)
        })
      }
    },
    mounted(){
      this.getMessagerData();
    }
  }
</script>

<style>
  body {
    margin: 0;
    background-color: #f9f9fa;
  }
</style>
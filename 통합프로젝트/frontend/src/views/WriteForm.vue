<template>
    <div>
        <h3>글을 작성하는 공간입니다</h3>
        <input type="text" v-model="title"><br>
        <textarea name="" id="" cols="30" rows="10" v-model="memo"></textarea><br>
        <button @click="addmemo">전송</button>

        <form action="/api/memo/writeform" method="post">
            <input type="text" name="title"><br>
            <textarea name="memo" id="" cols="30" rows="10"></textarea><br>
            <input type="submit" value="전송">
        </form>
    </div>
</template>
<script>
export default {
    data() {
        return {
            title:"",
            memo:""
        }
    },
    methods: {
        addmemo(){
            // post를 이용해서 서버로 값 전달
            this.$http.post('/api/memo', {
                data:{
                    title:this.title,
                    memo:this.memo
                }
            }).then((response)=> console.log(response.data))
            this.$router.push('/')
        }
    },
}
</script>
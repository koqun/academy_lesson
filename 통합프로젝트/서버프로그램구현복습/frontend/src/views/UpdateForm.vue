<template>
    <div>
        <h1>글을 수정하는 곳입니다</h1>
        <input type="text" v-model="memo.title"> <br>
        <textarea cols="30" rows="10" v-model='memo.memo'></textarea> <br>
        <button @click="updatememo">수정</button>
    </div>
</template>

<script>
export default {
    data () {
        return {
            memo : {
                title:"",
                memo:""
            }
        }
    },
    created() {
        // axios 값을 가져옴 단, id값에 따른 1개의 값 - get
        // 값을 받아와서 this.memo에 저장
        // $route.params.id 를 통해 memo의 id 값 전달
        this.$http.get(`/api/memo/${this.$route.params.id}`)
        .then((response)=>{
            this.memo = response.data
        })
    },
    methods : {
        // axios를 이용해 제출 버튼을 눌렀을때 값을 보내줌 - post
        updatememo() {
            this.$http.put('/api/memo/updateform',{
                data : {
                    // 객체 자체를 보내줌
                    memo : this.memo
                }
            }).then((response)=>{
                console.log(response.data)
            });
            // MemoList.vue(Home)으로 이동
            this.$router.push('/')
        }
    }
}
</script>
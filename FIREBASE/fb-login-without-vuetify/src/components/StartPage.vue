<template>
    <div>
        <h1>시작 페이지</h1>
        <a @click="fnDoGoogleLogin_Popup">구글 로그인</a><br>
        <a href="/Login">이메일 로그인</a>
    </div>
</template>

<script>
export default {
    methods: {
        fnDoGoogleLogin_Popup(){
            this.$store.dispatch("fnDoGoogleLogin_Popup", {
            })
        }
    }
}
</script>
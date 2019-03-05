<template>
    <div>
        <v-card 
        class="pa-3"
        v-for="(list, index) in todoList"
        :key="index"> 
            <!-- v-card : vueatify 카드와 그림자를 만들어주는 컴포넌트
                v-for : 똑같은 형태가 여러개 반복되는것
                :key="inde" 를 넣는 이유는 여러개 반복되기 때문에 순서를 찾아주기위해서 넣어준다.
                clas="pa-3" vueatify 카드의 효과중하나로 Padding All 1~5 패딩을 전방위로 1~5 숫자로 넣는다.-->
            <p> {{list.memo}} </p>
            <p> {{list.status}} </p>

            <v-btn
                v-if="list.status === 'create'"
                @click="$emit('statusControl', index, 'done')"
                 flat round color="green">완료</v-btn>
            <v-btn
            v-else
             @click="$emit('statusControl', index, 'create')"
             flat round color="blue">부활</v-btn>
            <v-btn 
            @click="$emit('statusControl', index, 'done')"
            flat round color="red">제거</v-btn>

        </v-card>
    </div>
</template>

<script>

export default {
    props: ["todoList"]
    
}
</script>

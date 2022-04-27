<template>
    <Page class="app">
        <ActionBar title="Calculator" backgroundColor="#000000" />
        <GridLayout backgroundColor="#000000" class="keyboard"
            columns="*, *, *, *" rows="*, *, *, *, *, *, *">
            <StackLayout row="0" col="0" colSpan="4" rowSpan='2'>
                <Label width='90%' height='90%' textWrap="true" class="output"
                    v-model="result" />
            </StackLayout>

            <Button class="btn" backgroundColor="#ff9113" text="+"
                @tap="input('+')" row="2" col="0" />
            <Button class="btn" backgroundColor="#ff9113" text="^"
                @tap="input('**')" row="2" col="1" />
            <Button class="btn" backgroundColor="#ff9113" text="C"
                @tap="alldelete()" row="2" col="2" colSpan="2" />

            <Button class="btn" text="-" backgroundColor="#ff9113"
                @tap="input('-')" row="3" col="0" />
            <Button class="btn" text="1" @tap="input('1')" row="3" col="1" />
            <Button class="btn" text="2" @tap="input('2')" row="3" col="2" />
            <Button class="btn" text="3" @tap="input('3')" row="3" col="3" />

            <Button class="btn" backgroundColor="#ff9113" text="*"
                @tap="input('*')" row="4" col="0" />
            <Button class="btn" text="4" @tap="input('4')" row="4" col="1" />
            <Button class="btn" text="5" @tap="input('5')" row="4" col="2" />
            <Button class="btn" text="6" @tap="input('6')" row="4" col="3" />

            <Button class="btn" backgroundColor="#ff9113" text="/"
                @tap="input('/')" row="5" col="0" />
            <Button class="btn" text="7" @tap="input('7')" row="5" col="1" />
            <Button class="btn" text="8" @tap="input('8')" row="5" col="2" />
            <Button class="btn" text="9" @tap="input('9')" row="5" col="3" />


            <Button class="btn" backgroundColor="#ff9113" text="="
                @tap="calc()" row="6" col="0" />
            <Button class="btn" text="," @tap="input('.')" row="6" col="1" />
            <Button class="btn" text="0" @tap="input('0')" row="6" col="2"
                colSpan="2" />

        </GridLayout>
    </Page>
</template>

<script>
    export default {
        data() {
            return {
                result: ""
            };
        },
        methods: {
            input: function(char) {
                this.result = this.result.toString();
                this.result += char;
            },
            calc: function() {
                try {
                    this.result = eval(this.result);
                    if (isNaN(this.result)) {
                        throw new Error();
                    }
                } catch {
                    this.result = "invalid input";
                }
            },
            alldelete: function() {
                this.result = "";
            }
        }
    };
</script>

<style scoped lang="scss">
    .btn {
        background-color: #000000;
        font-size: 35;
        margin: 10px;
        border-radius: 30;
    }

    .output {
        background-color: #000000;
        font-size: 35;
        color: #ffffff;
    }

    .btn:active {
        background-color: #9e9e9e;

    }
</style>
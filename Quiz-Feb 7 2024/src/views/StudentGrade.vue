<template>
    <h2>Batch 1 Hands-on Exam</h2>
    <div style="display: flex;">
        <input type="text" v-model="name">
        <input type="number" v-model="grade">
        <button @click="addGrade()">Add</button>
    </div>
    <table style="border: 1px solid black;">
        <thead>
            <tr>
                <th>Student Id</th>
                <th>Student Name</th>
                <th>Student Average</th>
            </tr>
        </thead>
        <tbody>
            <tr v-for="(grade, index) in grades" :key="index">
                <td v-bind:class="grade.average >= 75 ? 'whiteDiv' : 'redDiv'">{{ index + 1 }}</td>
                <td v-bind:class="grade.average >= 75 ? 'whiteDiv' : 'redDiv'">{{ grade.studname }}</td>
                <td v-bind:class="grade.average >= 75 ? 'whiteDiv' : 'redDiv'">{{ grade.average }}</td>
            </tr>
        </tbody>
    </table>
</template>

<script>
export default {
    data() {
        return {
            grades: [],
            name: "",
            grade: "",
            number: 0
        };
    },
    mounted() {
        // Initialize with default data
        this.grades.push({
            studname: "Levi",
            average: 75
        });
        this.number = this.grades.length;
        this.grades.push({
            studname: "Cuyos",
            average: 72
        });
        this.number = this.grades.length;
    },
    methods: {
        addGrade() {
            if (this.name === "" || this.grade === "") return;

            this.number++;
            this.grades.push({
                studname: this.name,
                average: this.grade
            });

            // Reset input fields after adding grade
            this.name = "";
            this.grade = "";
        }
    }
};
</script>

<style>
.whiteDiv {
    background: lime;
}
.redDiv {
    background: red;
}
</style>

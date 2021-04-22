<template>
    <div class="main">
        <div v-for="subject in subjects" :key="subject.name">
            <h2>{{ subject.name }}</h2>

            <ul>
                <li v-for="grade in subject.grades">{{ grade }}</li>
            </ul>

            Durchschnitt: {{ getAverage(subject.grades) }}
            <hr />
        </div>

        Gesamter Durschnitt: {{ totalAverage }}<br />
        Mangelpunkte: {{ pointsBelow4 }}
        <hr />
        {{ passed ? 'Bestanden!' : 'Nicht bestanden!' }}
    </div>
</template>

<script>
    export default {
        data: function() {
            return {
                subjects: [
                    {
                        name: "Mathematik",
                        grades: [5,4.7,3.5,4.1]
                    },
                    {
                        name: "Geschichte",
                        grades: [5.5,4.9,5.75]
                    },
                    {
                        name: "Physik",
                        grades: [2,2.7,4.3]
                    },
                    {
                        name: "Deutsch",
                        grades: [4.25,3.4,3.5]
                    },
                ]
            }
        },
        methods: {
            getAverage: function(grades) {
                let total = 0;

                grades.forEach(grade => total += grade);

                const avg = total / grades.length;
                return Math.round(avg * 2) / 2; // Round to 0.5
            },
        },
        computed: {
            totalAverage: function() {
                let subjectsTotal = 0;

                this.subjects.forEach(subject => {
                    subjectsTotal += this.getAverage(subject.grades);
                })

                const avg = subjectsTotal / this.subjects.length;
                return Math.round(avg * 2) / 2;
            },
            pointsBelow4: function() {
                let total = 0;
                this.subjects.forEach(subject => {
                    const subjectAvg = this.getAverage(subject.grades);

                    if (subjectAvg < 4) {
                        total += (4 - subjectAvg)
                    }
                });

                return total;
            },
            passed: function() {
                if (this.totalAverage < 4) {
                    return false;
                }
                if (this.pointsBelow4 > 1 && this.totalAverage < 4.2) {
                    return false;
                }
                if (this.pointsBelow4 > 2 && this.totalAverage < 4.5) {
                    return false;
                }

                return true;
            }
        }
    }
</script>

<style lang="scss">
    .main {
        max-width: 500px;
        margin: 0 auto;
        background-color: #eee;
        padding: 20px;

        h1 {
            text-align: center;
        }
    }
</style>

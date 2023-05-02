<template>
    <div class="container">
        <div class="row mt-5">
            <div class="col-md-12">
                <div class="card">
                    <div class="card-header">
                        <h5 class="card-title">
                            All Student
                            <RouterLink class="btn btn-info btn-sm float-end text-white" to="/students/create">Add Student
                            </RouterLink>
                        </h5>
                    </div>
                    <div class="card-body">
                        <table class="table table-bordered">
                            <thead>
                                <tr>
                                    <th scope="col">#</th>
                                    <th scope="col">Full name</th>
                                    <th scope="col">Course</th>
                                    <th scope="col">Phone</th>
                                    <th scope="col">email</th>
                                    <th scope="col">Handle</th>
                                </tr>
                            </thead>
                            <tbody v-if="this.students.length > 0">
                                <tr v-for="(student, index) in this.students" :key="index">
                                    <td>{{ student.id }}</td>
                                    <td>{{ student.name }}</td>
                                    <td>{{ student.course }}</td>
                                    <td>{{ student.phone }}</td>
                                    <td>{{ student.email }}</td>
                                    <td>
                                        <a href="" class="btn btn-info btn-sm">Edit</a>
                                        <a href="" class="btn btn-danger btn-sm">Delete</a>
                                    </td>
                                </tr>
                            </tbody>
                            <tbody v-else>
                                <tr>
                                    <td colspan="6">
                                        <div class='container mt-5 text-center'>
                                            <div class="spinner-border text-info" role="status">
                                                <span class="visually-hidden">Loading...</span>
                                            </div>
                                            <p class='mt-2 text-muted'>Loading...</p>
                                        </div>
                                    </td>
                                </tr>
                            </tbody>
                        </table>
                    </div>
                </div>
            </div>
        </div>

    </div>
</template>
<script>
import axios from 'axios';

export default {
    name: 'students',
    data() {
        return {
            students: []
        }
    },
    mounted() {
        console.log('i am mounted');
        this.getStudents()
    },
    methods: {
        getStudents() {
            axios.get('https://apiv1.mamungroup.net/api/students')
                .then(res => {
                    this.students = res.data.data
                    console.log(this.students);
                })
        }
    }
}
</script>
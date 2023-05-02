<template>
    <div class="container">
        <div class="row mt-5">
            <div class="col-md-12">
                <div class="card">
                    <div class="card-header">
                        <h5 class="card-title">
                            Add New Student 
                            <RouterLink class="btn btn-info btn-sm float-end text-white" to="/students">All Student</RouterLink>
                        </h5>
                    </div>
                    <div class="card-body">
                        <div class="mb-3">
                            <label for="name" class="form-label">Full name</label>
                            <input type="text" v-model="model.student.name" class="form-control" id="name">
                        </div>
                        <div class="mb-3">
                            <label for="course" class="form-label">Course name</label>
                            <input type="text" v-model="model.student.course" class="form-control" id="course">
                        </div>
                        <div class="mb-3">
                            <label for="email" class="form-label">Email</label>
                            <input type="email" v-model="model.student.email" class="form-control" id="email">
                        </div>
                        <div class="mb-3">
                            <label for="phone" class="form-label">Phone</label>
                            <input type="text" v-model="model.student.phone" class="form-control" id="phone">
                        </div>
                        <div class="mb-3">
                            <label for="address" class="form-label">Address</label>
                            <input type="text" v-model="model.student.address" class="form-control" id="address">
                        </div>
                    </div>
                    <div class="card-footer">
                            <button type="button" @click="saveStudent" class="btn btn-info btn-sm float-end text-white">Save</button>
                    </div>
                </div>
            </div>
        </div>

    </div>
</template>
<script>
import axios from 'axios'
    export default{
        name:'studentsCreate',
        data(){
            return {
                model:{
                    student:{
                        name:'',
                        course:'',
                        phone:'',
                        email:'',
                        address:''
                    }
                }
            }
        },
        methods:{
            saveStudent(){
                axios.post('https://apiv1.mamungroup.net/api/students',this.model.student)
                .then(res=>{
                    console.log(res);
                    alert(res.data.message);
                    this.model.student = {
                        name:'',
                        course:'',
                        phone:'',
                        email:'',
                        address:''
                    }
                })
            }
        }
    }
</script>
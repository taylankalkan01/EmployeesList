<template>
    <div class = "container">
            
            <h1 class = "text-center"> Employees List</h1>

            <table class = "table table-striped">
                <thead>
                    <tr>
                        <th> Employee First Name</th>
                        <th> Employee Last</th>
                        <th> Employee Email</th>
                    </tr>

                </thead>
                <tbody>
                    <tr v-for="employee in employees" v-bind:key="employee.firstName">
                        <td> {{employee.firstName }}</td>
                        <td> {{employee.lastName}}</td>    
                        <td> {{employee.email}}</td>
                    </tr>
                </tbody>
            </table>
        </div>
</template>

<script>

import EmployeeService from '../services/EmployeeServce';

export default {
    name: 'Employees',
    data(){
        return {
            employees: []
        }
    },
    methods: {
        getAllEmployees(){
            EmployeeService.getAllEmployees().then((response) => {
                this.employees = response.data;   
            });
        }
    },
    created() {
        this.getAllEmployees();
    }
}

</script>
<template>

  <h1>Vue 3 jQuery DataTable Example Tutorial - Tutsmake.com</h1>

   <table class="table table-hover table-bordered" id="example">
    <thead>
      <tr>
        <th>ID</th>
        <th>Name</th>
        <th>Email</th>
        <th>Job Title</th>
      </tr>
    </thead>
  </table>
</template>

<script>
// Bootstrap and jQuery libraries
import 'bootstrap/dist/css/bootstrap.min.css'
import 'jquery/dist/jquery.min.js'
// Datatable Modules
import 'datatables.net-dt/js/dataTables.dataTables'
import 'datatables.net-dt/css/jquery.dataTables.min.css'
import $ from 'jquery'

import axios from 'axios'
export default {
  name: 'MyDataTable',
  mounted () {
    // API Call
    $('#example').DataTable({
      serverSide: true,
      columns: [
        { data: 'id' },
        { data: 'name' },
        { data: 'email' },
        { data: 'job' }
      ],
      ajax: function (data, callback, settings) {
        // you have to use your own API
        axios
          .get('users?' + $.param(data))
          .then((res) => {
            console.log(res)
            callback(res)
          })
      }
    })
  }
}
</script>

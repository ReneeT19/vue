<!-- in mustaches -->
{{ message | capitalize }}

<!-- in v-bind -->
<div v-bind:id="rawId | formatId"></div>

filters: {
  capitalize: function (value) {
    if (!value) return ''
    value = value.toString()
    return value.charAt(0).toUpperCase() + value.slice(1)
  }
}

Vue.filter('capitalize', function (value) {
  if (!value) return ''
  value = value.toString()
  return value.charAt(0).toUpperCase() + value.slice(1)
})

new Vue({
  // ...
})

<!-- john will print John -->
<!-- Filters can be chained -->
{{ message | filterA | filterB }}
<!-- Filters can take arguments -->
{{ message | filterA('arg1', arg2) }}


class Post {
  constructor(title, link, author, img) {
    this.title = title;
    this.link = link;
    this.author = author;
    this.img = img;
  }
}

const app = new Vue ({
  el: '#app',
  data: {
    search: '',
    postList : [
      new Post(
        'Vue.js', 
        'https://vuejs.org/', 
        'Chris', 
        'https://vuejs.org//images/logo.png'
      ),
      new Post(
        'React.js', 
        'https://facebook.github.io/react/', 
        'Tim',
        'https://daynin.github.io/clojurescript-presentation/img/react-logo.png'
      ),
      new Post(
        'Angular.js', 
        'https://angularjs.org/', 
        'Sam', 
        'https://angularjs.org/img/ng-logo.png'
      ),
      new Post(
        'Ember.js', 
        'http://emberjs.com/', 
        'Rachel',
        'http://www.gravatar.com/avatar/0cf15665a9146ba852bf042b0652780a?s=200'
      ),
      new Post(
        'Meteor.js', 
        'https://www.meteor.com/', 
        'Chris', 
        'http://hacktivist.in/introduction-to-nodejs-mongodb-meteor/img/meteor.png'
      ),
      new Post(
        'Aurelia', 
        'http://aurelia.io/', 
        'Tim',
        'https://cdn.auth0.com/blog/aurelia-logo.png'
      ),
      new Post(
        'Node.js', 
        'https://nodejs.org/en/', 
        'A. A. Ron',
        'https://code-maven.com/img/node.png'
      ),
      new Post(
        'Pusher', 
        'https://pusher.com/', 
        'Alex', 
        'https://avatars1.githubusercontent.com/u/739550?v=3&s=400'
      ),
      new Post(
        'Feathers.js', 
        'http://feathersjs.com/', 
        'Chuck',
        'https://cdn.worldvectorlogo.com/logos/feathersjs.svg'
      ),
]
  },
  computed: {
    filteredList() {
      return this.postList.filter(post => {
        return post.title.toLowerCase().includes(this.search.toLowerCase())
      })
    }
  }
})



<!-- Sorting -->
const sortedArray: Test[] = unsortedArray.sort((obj1, obj2) => {
  if (obj1.value > obj2.value) {
    return 1;
  } else if (obj1.value < obj2.value) {
    return -1;
  }
  return 0;
});



//Sorting Table
<template>
    <table>
        <thead>
            <tr>
                <th @click="sortByColumn('id')">ID
                    <span v-if="sortColumn == 'id'" class="material-icons"></span>
                    <span v-else class="material-icons">sort</span>
                </th>
                <th @click="sortByColumn('name')">Name
                    <span v-if="sortColumn == 'name'" class="material-icons"></span>
                    <span v-else class="material-icons">sort</span>
                </th>
            </tr>
        </thead>
        <tbody>
            <tr v-for="row in tableData" :key="row.id">
                <td></td>
                <td></td>
            </tr>
        </tbody>
    </table>
</template>

<script lang="ts">
import { defineComponent, ref } from 'vue'
export default defineComponent({
    setup() {
        interface dataInfo {
            id: number,
            name: string
        }
        let data: Array<dataInfo> = [
            {"id": 1, "name": "Phil"},
            {"id": 2, "name": "Bobby"},
            {"id": 3, "name": "Susie"},
        ];
        const tableData = ref(data);
        const sortColumn = ref("id");
        const sortDirection = ref(1);
        const arrowIconName = ref("arrow_drop_up");
        const sortByColumn = (columnName: keyof dataInfo) => {
            sortColumn.value = columnName;
            sortDirection.value = -1 * sortDirection.value;
            if (sortDirection.value == 1) {
                arrowIconName.value = "arrow_drop_up";
                tableData.value.sort((a, b) => (a[columnName] > b[columnName] ? 1 : -1));
            } else {
                arrowIconName.value = "arrow_drop_down";
                tableData.value.sort((a, b) => (a[columnName] < b[columnName] ? 1 : -1));
            }
        }
        return {tableData, sortColumn, sortDirection, arrowIconName, sortByColumn};
    },
})
</script>

<style scoped>
table {
    border-collapse: collapse;
    margin: auto;
    box-shadow: 0 0 20px rgba(0, 0, 0, 0.15);
}
thead tr {
    background-color: gray;
    color: white;
}
tbody tr {
    border-bottom: 1px solid black;
}
th, td {
    padding: 12px 15px;
}
.material-icons {
    vertical-align: -6px;
}
th {
    cursor: pointer;
}
</style>
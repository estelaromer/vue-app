Vue.component('app-header', {
  template: '<div><h1>Component Title</h1></div>'
});

Vue.component('app-footer', {
  template: '<div><h4>testdriven.io (2019)</h4></div>'
});

var vm = new Vue({
    el: '#vue_app',
    data: {
        navTitle: 'Vue Course',
        footerMessage: 'testdriven.io (2019)',
        users: [
            'user1',
            'employee17',
            'Bob',
            'Sara',
            'Garfield',
        ],
        displayUsers: true,
        newUser: '',
        searchName: '',
        usersTextColor: [
            'white',
            'white',
            'white',
            'white',
            'white',
        ],
    },
    methods: {
        changeDisplay() {
            this.displayUsers = !this.displayUsers;
        },
        addNewUser(newUserInput) {
            if (newUserInput !== '') {
                // Add the user to the local array of users
                this.users.push(newUserInput);
                // Clear the value of the new user's name
                this.newUser = '';
                // Add the styling for the new user to highlight the new user only
                for (var i = 0; i < this.usersTextColor.length; i++) {
                    this.usersTextColor[i] = 'white';
                }
                this.usersTextColor.push('darkgreen');
            }
        },
    },
    computed: {
        numberOfUsersText() {
            return 'There are ' + this.users.length + ' users.';
        },
        searchResults() {
            if (this.searchName != '') {
                return this.users.filter(el => el.match(this.searchName))
            } else {
                return '';
            }
        },
        searchTextClass() {
            if (this.searchName != '') {
            return 'searchTitleBold';
            } else {
            return 'searchTitleNormal';
            }
        },
    },
});
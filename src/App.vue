<template>
  <section>
    <header>
      <h1>Contact List</h1>
    </header>
    <new-friend @add-contact="addContact"></new-friend>
    <ul>
      <friend-contact
        v-for="friend in friends"
        :key="friend.id"
        :id="friend.id"
        :name="friend.name"
        :phone-number="friend.phone"
        :email-address="friend.email"
        :is-favorite="friend.isFavorite"
        @toggle-favorite="toggleFavoriteStatus"
        @delete="deleteContact"
      ></friend-contact>
    </ul>
  </section>
</template>

<script>
export default {
  data() {
    return {
      friends: [
        {
          id: 'oana',
          name: 'Oana Nistor',
          phone: '0741 123 456',
          email: 'oana@yahoo.com',
          isFavorite: true,
        },
        {
          id: 'alex',
          name: 'Alex Nistor',
          phone: '0741 789 456',
          email: 'alex@yahoo.com',
          isFavorite: false,
        },
        {
          id: 'ema',
          name: 'Ema Nistor',
          phone: '0741 999 999',
          email: 'ema@yahoo.com',
          isFavorite: false,
        },
      ],
    };
  },

  methods: {
    toggleFavoriteStatus(friendId) {
      const identifiedFriend = this.friends.find(
        (friend) => friend.id === friendId
      );
      identifiedFriend.isFavorite = !identifiedFriend.isFavorite;
    },
    addContact(name, phone, email) {
      //create a new object with the users input data
      const newFriendContact = {
        id: new Date().toISOString(),
        name: name,
        phone: phone,
        email: email,
        isFavorite: false,
      };
      this.friends.push(newFriendContact); //push it to the friends array
    },
    deleteContact(friendId) {
      this.friends = this.friends.filter((friend) => friend.id !== friendId);
      //filter will return a new array based on the array we are calling it, except for the elements you are filtering out
      //if funtion returns true, element is kept.
      //if function returns false, element is deleted
      //if id's are equal, element gets deleted
      //if id's are not the same, we keep the element
    },
  },
};
</script>

<style>
* {
  box-sizing: border-box;
}

html {
  font-family: Verdana, Geneva, Tahoma, sans-serif;
  background-color: #efefef;
}

body {
  margin: 0;
}

header {
  margin: 3rem auto;
  color: #064635;
  text-align: center;
  width: 90%;
  max-width: 40rem;
  font-size: larger;
}

#app ul {
  margin: 0;
  padding: 0;
  list-style: none;
}

#app li,
#app form {
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.26);
  margin: 1rem auto;
  border-radius: 6px;
  padding: 0.5rem;
  text-align: center;
  width: 90%;
  max-width: 40rem;
  background-color: #f4eea9;
}

#app form {
  background-color: #f0bb62;
}

#app h2 {
  font-size: 1.5rem;
  border-bottom: 2px solid #ccc;
  color: #2c2b2c;
  margin: 0 0 1rem 0;
  padding: 10px;
}

#app button {
  font-size: smaller;
  font-weight: 700;
  cursor: pointer;
  border: 1px solid #2bf36e;
  background-color: #519259;
  color: #2c2b2c;
  padding: 0.05rem 1rem;
  box-shadow: 1px 1px 2px rgba(0, 0, 0, 0.26);
  border-radius: 5px;
  padding: 6px;
  margin: 5px;
}

#app button:hover,
#app button:active {
  background-color: #064635;
  border-color: #519259;
  box-shadow: 1px 1px 4px rgba(0, 0, 0, 0.26);
  color: white;
}

#app input {
  font: inherit;
  padding: 0.15rem;
}

#app label {
  font-weight: bold;
  margin-right: 1rem;
  width: 7rem;
  display: inline-block;
}

#app form div {
  margin: 1rem 0;
}

#app .contact-details {
  background-color: white;
}
</style>

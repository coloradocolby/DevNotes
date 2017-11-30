# Firebase

Some example firebase code

```
database.ref('expenses').on('child_removed', (snapshot) => {
  console.log(snapshot.key, snapshot.val());
});

database.ref('expenses').on('child_changed', (snapshot) => {
  console.log(snapshot.key, snapshot.val());
});

database.ref('expenses').on('child_added', (snapshot) => {
  console.log(snapshot.key, snapshot.val());
});

database.ref('expenses').on('value', (snapshot) => {
    const expenses = []

    snapshot.forEach((childSnapshot) => {
      expenses.push({
        id: childSnapshot.key,
        ...childSnapshot.val()
      });
    });
    console.log(expenses);
  });

database.ref('expenses')
  .once('value')
  .then((snapshot) => {
    const expenses = [];

    snapshot.forEach((childSnapshot) => {
      expenses.push({
        id: childSnapshot.key,
        ...childSnapshot.val()
      });
    });
    console.log(expenses);
  });

database.ref('expenses').push({
  description: 'Dinner',
  note: 'was fun!',
  amount: 20,
  createdAt: 0
});

database.ref('notes/-KyTqfUSHYg0YArS9sNw').remove();

database.ref('notes/-KyTqfUSHYg0YArS9sNw').update({
  body: 'buy food'
});

database.ref('notes').push({
  title: 'Course Topics',
  body: 'React Native, Angular, Python'
});

const firebaseNotes = {
  notes: {
    idone: {
      title: 'test',
      body: 'this is my notes'
    },
    idtwo: {
      title: 'asdfasdf',
      body: 'asdfasdf'
    }
  }
}

const notes = [{
  id: '12',
  title: 'First note',
  body: 'This is my note'
},{
  id: '44',
  title: 'Another note',
  body: 'This is my note'
}]

database.ref('notes').set(firebaseNotes);

const onValueChange = database.ref()
  .on('value', (snapshot) => {
    let val = snapshot.val();
    console.log(`${val.name} is a ${val.job.title} at ${val.job.company}`)
  }, (err) => {
    console.log('Error', err);
  });

setTimeout(() => {
  database.ref('job/company').set('Pariveda');
}, 3000);

const onValueChange = database.ref()
  .on('value', (snapshot) => {
    console.log(snapshot.val());
  }, (error) => {
    console.log('error with data fetching', error);
  });

setTimeout(() => {
  database.ref('age').set(29)
}, 3500);

setTimeout(() => {
  database.ref().off(onValueChange);
}, 7000);

setTimeout(() => {
  database.ref('age').set(30)
}, 10500);


database.ref('location/city')
  .once('value')
  .then((snapshot) => {
    console.log(snapshot.val());
  }).catch((err) => {
    console.log('Error', err);
  });


database.ref().set({
  name: 'Colby Thomas',
  age: 23,
  stressLevel: 6,
  isSingle: false,
  job: {
    title: 'Tech Consultant',
    company: 'Pariveda Solutions'
  },
  location: {
    city: 'Dallas',
    country: 'United States'
  }
}).then(() => {
  console.log('Data is saved');
}).catch((err) => {
  console.log('This failed:', err);
});

database.ref().set('This is my data');
database.ref('age').set(24);
database.ref('location/city').set('Dallas');

database.ref('attributes').set({
  height: 71,
  weight: 185
}).then(() => {
  console.log('second set call worked');
}).catch((err) => {
  console.log('Second set failed', err);
});


database.ref()
.remove()
.then(() => {
  console.log('removed');
}).catch((err) => {
  console.log('removing error', err);
});

same as remove()
database.ref('isSingle').set(null);

database.ref().update({
  name: 'Mike',
  age: 56,
  job: 'Software Developer', // sets something for first time
  isSingle: null
});

database.ref().update({
  job: 'Software Developer', // sets something for first time
  'location/city': 'Dallas'
});

database.ref().update({
  stressLevel: 9,
  'job/company': 'Amazon',
  'location/city': 'Seattle'
});
```
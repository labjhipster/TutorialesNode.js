mongo "mongodb+srv://cluster0.cyjte.mongodb.net/test" --username

use test;

db.places.insertMany([
	{
		"name": "Parque del Retiro",
		"location": {
			"type": "Point",
			"coordinates": [-3.674908, 40.411335]
		}
	},
	{
		"name": "Puerta del Sol",
		"location": {
			"type": "Point",
			"coordinates": [-3.703339, 40.416729]
		}
	},
	{
		"name": "Palacio Real",
		"location": {
			"type": "Point",
			"coordinates": [-3.7083305, 40.41749833]
		}
	}
]);

db.places.find( {} );

db.places.createIndex({ "location": "2dsphere" });

db.places.find(
	{
	  "location": {
		"$nearSphere": {
		  "$geometry": {
			"type": "Point",
			"coordinates": [-3.674948, 40.411325]
		  },
		  "$maxDistance": 200
		}
	  }
	}
);


https://3000-green-cobra-59edpp8j.ws-eu03.gitpod.io/api/places/

https://3000-green-cobra-59edpp8j.ws-eu03.gitpod.io/api/places/near?long=-3.674948&latt=40.411325&distance=2000

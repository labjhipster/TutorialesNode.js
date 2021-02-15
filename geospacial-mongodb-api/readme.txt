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



http://localhost:3000/api/places?long=-3.674948&lat=40.411325
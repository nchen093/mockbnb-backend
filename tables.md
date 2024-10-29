Table user {
id integer [primary key]
reviews integer
bookings integer
spots integer
firstName varchar
lastName varchar
email varchar
userName varchar
}

Table review {
id integer
spotId integer
review varchar
stars integer
reviewImages integer
createdAt datetime
updatedAt datetime
}

Table reviewImage {
id integer
imageUrl varchar
}

Table spot {
id integer [primary key]
ownerId integer
reviewId integer
address varchar
city varchar
state varchar
country varchar
lat decimal
lng decimal
numReviews integer
name varchar
description varchar
price decimal
createdAt datetime
updatedAt datetime
avgRating float
previewImage varchar
spotImages integer
}

Table booking {
id integer [primary key]
spotId integer
renterId integer
ownerId integer
startDate date
endDate date
}

Table spotImages {
id integer [primary key]
imageUrl varchar
}

Ref: "spot"."spotImages" < "spotImages"."id"
Ref: "spot"."reviewId" < "review"."id"
Ref: "review"."reviewImages" < "reviewImage"."id"
Ref: "review"."spotId" < "spot"."id"
Ref: "user"."id" < "booking"."renterId"
Ref: "user"."id" < "booking"."ownerId"
Ref: "booking"."spotId" < "spot"."id"
Ref: "user"."id" < "spot"."ownerId"
Ref: "user"."reviews" < "review"."id"
Ref: "user"."bookings" < "booking"."id"
Ref: "user"."spots" < "spot"."id"

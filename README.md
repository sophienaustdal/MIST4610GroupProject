# Group 1 MIST4610 Group Project 1

## Team Name
21482 Group 1

## Team Members
1. Sophie Naustdal https://github.com/sophienaustdal/MIST4610GroupProject.git
2. Rachel Chuan
3. Riley Cook https://github.com/rileyacook/4610Proj1.git
4. Chidera Nwosu
5. Coleman Vaughn

## Scenario Description
Our company, Dawg Fitness, is a large fitness enterprise with multiple gym locations across the United States, with each gym serving as the core of our operations. While all gyms operate under Dawg Fitness, each location offers tailored services to meet the diverse needs of its members. Our goal is to create a relational database that connects all relevant entities across the business. This database will manage key information such as gym details, member profiles, trainers, equipment inventory, class schedules, membership plans, payment history, and survey feedback. By leveraging this data, we aim to structure queries that provide valuable insights for improving and growing Dawg Fitness’s operations.

## Data Model
Explanation of data model:

Our model's most center-based entity is our Gym entity. The Gym entity represents each of Dawg Fitness's distinct gym locations across the United States. Its attributes include a unique identifier, location, phone number, and email. Since our gym table is our central point, we have multiple relationships stemming from the Gym entity: Equipment, Staff, and Members.

Equipment is directly related to Gyms, as equipment and resources are the main points of operation in gyms. A unique ID number is assigned to each piece of equipment, along with the name, status, and age of each piece. Equipment belongs to only one gym, so the gymID, which identifies the gym where the equipment is located, is present for each piece of equipment. Although equipment can only belong to one gym, a gym can have multiple pieces of equipment representing a one-to-many relationship.

Our Staff entity tracks all non-trainer employees within our organization. To keep up with each individual staff member, we have assigned them a unique ID number. Other important information includes name, date of birth, contact information, position, salary, and the duration of their employment at Dawg Fitness. Each staff member is only able to work for one gym, hence the gymID being present for each row of staff members. Since gyms require many staff members to operate, this results in a one-to-many relationship.

Our Members table has a one-to-many relationship with the Gym table because our gym locations can be home to many members, but each member belongs to only one Dawg Fitness location. We assign a unique identifier to each member and track basic information such as name, personal details, contact information, and address. Although the Members table is not the central entity, it has the most relationships with other tables. There is a relationship with MembershipPlans that identifies which of our multiple membership options a member is under; a member can have one plan, while a plan can have multiple members. GymID is also present within the table to identify which gym our members are associated with. Members have the option to sign up for group classes taught by our trainers. Since members can sign up for multiple classes and classes can have multiple members, the associative entity "ClassRegistration" connects the two. Additionally, each member has their own payment information associated with their account.

Dawg Fitness offers a variety of membership plans to fit the different needs of our members. Each plan requires a unique identifier to differentiate between plans and their details. Each plan is named and assigned a monthly fee, along with a description of the accessibility offered by the plan.

Regarding the Payments entity, each payment requires a unique identifier and tracks the associated fee a member has paid for gym access on that date. The member's payment method used is also recorded in this table along with the date they submitted the payment. MemberID is present within the table to associate each payment with a single member, but members make multiple payments, as there are monthly dues.

Though our trainers operate under the name "Dawg Fitness," they are a separate entity functioning independently. Like staff members, trainers have an ID number to track each individual trainer. Necessary details include name, salary, tenure at Dawg Fitness, area of expertise, and contact information. Trainers are associated with both Members and Classes in a many-to-many relationship. Trainers can have multiple one-on-one sessions with different members, recorded in the PrivateSessions table. Since trainers can teach multiple classes and each class type can have multiple trainers, we use the associative entity "TrainerSchedule."

Our Classes table is straightforward, tracking each class by classID, class name, the room where the class is taught, and the maximum number of members that can enroll. The Classes table is related to multiple tables: TrainerSchedule, ClassRegistration, and Surveys. Each class can have multiple Survey entries, registrations, and TrainerSchedule associations.

To track member satisfaction and their experience with classes, we created the Surveys table. Each survey requires a unique primary key, which is a survey ID number. To track recent trends in our classes, we include a date-submitted attribute. To assess satisfaction, we implement a 1-5 rating system. The classID foreign key is present to attribute ratings and feedback to each class.

ClassRegistration is one of our three associative entities. Many members can take many different classes, thus this many-to-many relationship results in an associative entity. The composite primary key is made up of classID and memberID which tracks which classes and members are associated with each one another. RegistrationID is also a primary key, to represent each unique case of a member signing up for a class. The class name is also present in this table to easily signify which class a member has been registered for. The date of the class is also present as members can take the same class many times over various dates.

TrainerSchedule is the associative entity linking trainers to the classes they teach. Many trainers can teach many classes. Similar to the ClassRegistration table, there are three primary keys, two of which originate from other tables. The trainerID is necessary to identify which trainer is teaching a class, and classID determines which class is within the trainer's schedule. The third primary key, scheduleID, represents each unique case of a trainer teaching a class. The date of a class they teach is also represented as trainers can teach the same class many times over many dates.

PrivateSessions is designed for members interested in one-on-one training with a trainer. Many members can have many private sessions with trainers. The composite primary key originates from the Members table with memberID and the Trainers table with trainerID, allowing each session to track which member is working with which trainer. The PrivateSessionID is a table-specific primary key that represents each unique pairing of a member and the trainer they are to have a one-on-one session with. Again, the date of the private session is included, as members can have many different private sessions with the same trainer.

<img width="645" alt="Screenshot 2025-03-16 at 12 44 34 AM" src="https://github.com/user-attachments/assets/376abce4-404e-4845-a157-602aa907a245" />


## Data Dictionary
<img width="779" alt="Screenshot 2025-03-13 at 7 34 19 PM" src="https://github.com/user-attachments/assets/36439e9f-7eef-47ae-bd71-4de45dc5f2e8" />

<img width="779" alt="Screenshot 2025-03-13 at 7 58 57 PM" src="https://github.com/user-attachments/assets/32b80385-4c35-4fa7-83c6-26a8a35536c6" />

<img width="795" alt="Screenshot 2025-03-16 at 12 50 11 AM" src="https://github.com/user-attachments/assets/a90603b8-40a8-4b55-a3fc-59d2bae738d2" />


## Queries

## Database Information
Name of the Database: ns_Sp25_21482_Group1

Additional information: Each query listed above is marked in the database using stored procedures which can be called using the following format: CALL TP_Q1();

The Filter needs to be tested with the following test cases

Filters
- Status
- CreatedBy
- Author
- Course

```
  A Full Url For this would be 
  {{url}}/api/event/?page_num=1&state=Scheduled,Ongoing&course_id=140&items=100&organization_id=72&trainer_id=118
```

status: Completed, Scheduled, Ongoing
trainer: trainer_id which is integer
created_by: is the attribute being used which is the user id which is integer
course: this is the primary key id of the course


Test Cases Done
1. Only By Status: {{url}}/api/event?page_num=1&state=Scheduled (All Passed)
2. Only By Course: {{url}}/api/event?page_num=1&state=Scheduled&course_id=140,145  (All Passed)
3. Only By Trainer: {{url}}/api/event?page_num=1&items=100&organization_id=72&trainer_id=170 (All Passed)
4. Only By created_by: 
   - 4a(Created by me). {{url}}/api/event?page_num=1&items=100&organization_id=72&created_by=108 (All Passed)
   - 4b(Created by All). {{url}}/api/event?page_num=1&items=100&organization_id=72(All Passed)

So Biggest url that can connect the combination would be:
```
{{url}}/api/event?page_num=1&course_id=140,145&items=100&organization_id=72&trainer_id=170&created_by=108

page_num =========> this is the attribute for the Page Num selection
course_id ========> this can be course_ids can be multiple by comma seperations
items ============> this is the integer to fetch number of items in one page
organization_id ==> this is the id of the organization
trainer_id =======> this is the user_id created for that trainer
created_by =======> this would be comma seperated user_ids for filtering the data .
```


All the Combinations are giving the right results
```
    url: {{url}}/api/event?page_num=1&course_id=140,145&items=100&organization_id=72&trainer_id=170
    HTTP VERB: GET
    response:
    {
        "status": 200,
        "message": "Found",
        "data": {
            "Event_data": [
                {
                    "id": 120,
                    "event_id": "EVE-0010",
                    "training_record": null,
                    "user": 108,
                    "event_role": "Admin",
                    "course": {
                        "id": 145,
                        "course_id": "COU-120",
                        "name": "Golang Dev Tools",
                        "description": "course",
                        "mode": "Online",
                        "type": "Training",
                        "duration": 30,
                        "validity": 12,
                        "auth_by": "auth",
                        "license": true,
                        "has_cert": true,
                        "language": null,
                        "is_deleted": false,
                        "is_archived": false,
                        "user": 108,
                        "organization": 72
                    },
                    "organization": 72,
                    "training_status": null,
                    "type": "Certification",
                    "mode": "Online",
                    "state": "Scheduled",
                    "trainer_status": "pending",
                    "reminder": 30,
                    "start_date": "Jan 02 2020",
                    "end_date": "Jun 02 2020",
                    "start_time": "08:30 AM",
                    "end_time": "06:30 PM",
                    "lat_long": null,
                    "max_participants": 20,
                    "trainer": {
                        "id": 170,
                        "email": "int-train9012@yopmail.com",
                        "name_title": "Mr",
                        "first_name": "veftor",
                        "last_name": "k",
                        "file_name": null,
                        "phone": "8050284789",
                        "url": "https://tracksafety-dev.s3.amazonaws.com/blank-4px7pBY5DA-QAHS9cqWTj.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAVYLUBLBZTZO4EZNR%2F20200522%2Fus-east-1%2Fs3%2Faws4_request&X-Amz-Date=20200522T070759Z&X-Amz-Expires=3600&X-Amz-SignedHeaders=host&X-Amz-Signature=4f1972f7461f49362561cdf669123af6fed07163ca2cdef68334485e76ad87a1",
                        "is_deleted": false,
                        "is_active": true
                    },
                    "location": {
                        "id": 25,
                        "address_1": "GR-GrandStreet",
                        "address_2": "Leiccal Circle",
                        "city": "Bengaluru",
                        "zip_code": null,
                        "country": "ind",
                        "state": "Karantaka",
                        "lat_long": {
                            "lat": 123.444,
                            "long": 94.0949494
                        },
                        "type": 4,
                        "is_deleted": false,
                        "user": 108,
                        "organization": 72
                    },
                    "attendees": {
                        "max_participants": 20,
                        "accepted": 0,
                        "pending": 0,
                        "declined": 0,
                        "vacancy": 20,
                        "waiting_list": 0
                    },
                    "is_manual_entry": false
                },
                {
                    "id": 119,
                    "event_id": "EVE-0009",
                    "training_record": null,
                    "user": 108,
                    "event_role": "Admin",
                    "course": {
                        "id": 140,
                        "course_id": "COU-123",
                        "name": "React Dev-III Tools",
                        "description": "course",
                        "mode": "Online",
                        "type": "Certification",
                        "duration": 30,
                        "validity": 12,
                        "auth_by": "auth",
                        "license": true,
                        "has_cert": true,
                        "language": null,
                        "is_deleted": false,
                        "is_archived": false,
                        "user": 108,
                        "organization": 72
                    },
                    "organization": 72,
                    "training_status": null,
                    "type": "Training",
                    "mode": "Online",
                    "state": "Scheduled",
                    "trainer_status": "pending",
                    "reminder": 30,
                    "start_date": "Jan 02 2020",
                    "end_date": "Jun 02 2020",
                    "start_time": "08:30 AM",
                    "end_time": "06:30 PM",
                    "lat_long": null,
                    "max_participants": 20,
                    "trainer": {
                        "id": 170,
                        "email": "int-train9012@yopmail.com",
                        "name_title": "Mr",
                        "first_name": "veftor",
                        "last_name": "k",
                        "file_name": null,
                        "phone": "8050284789",
                        "url": "https://tracksafety-dev.s3.amazonaws.com/blank-4px7pBY5DA-QAHS9cqWTj.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAVYLUBLBZTZO4EZNR%2F20200522%2Fus-east-1%2Fs3%2Faws4_request&X-Amz-Date=20200522T070759Z&X-Amz-Expires=3600&X-Amz-SignedHeaders=host&X-Amz-Signature=4f1972f7461f49362561cdf669123af6fed07163ca2cdef68334485e76ad87a1",
                        "is_deleted": false,
                        "is_active": true
                    },
                    "location": {
                        "id": 25,
                        "address_1": "GR-GrandStreet",
                        "address_2": "Leiccal Circle",
                        "city": "Bengaluru",
                        "zip_code": null,
                        "country": "ind",
                        "state": "Karantaka",
                        "lat_long": {
                            "lat": 123.444,
                            "long": 94.0949494
                        },
                        "type": 4,
                        "is_deleted": false,
                        "user": 108,
                        "organization": 72
                    },
                    "attendees": {
                        "max_participants": 20,
                        "accepted": 0,
                        "pending": 0,
                        "declined": 0,
                        "vacancy": 20,
                        "waiting_list": 0
                    },
                    "is_manual_entry": false
                },
                {
                    "id": 117,
                    "event_id": "EVE-0007",
                    "training_record": null,
                    "user": 108,
                    "event_role": "Admin",
                    "course": {
                        "id": 140,
                        "course_id": "COU-123",
                        "name": "React Dev-III Tools",
                        "description": "course",
                        "mode": "Online",
                        "type": "Certification",
                        "duration": 30,
                        "validity": 12,
                        "auth_by": "auth",
                        "license": true,
                        "has_cert": true,
                        "language": null,
                        "is_deleted": false,
                        "is_archived": false,
                        "user": 108,
                        "organization": 72
                    },
                    "organization": 72,
                    "training_status": null,
                    "type": "Training",
                    "mode": "Online",
                    "state": "Scheduled",
                    "trainer_status": "pending",
                    "reminder": 30,
                    "start_date": "Jan 02 2020",
                    "end_date": "Jun 02 2020",
                    "start_time": "08:30 AM",
                    "end_time": "06:30 PM",
                    "lat_long": null,
                    "max_participants": 20,
                    "trainer": {
                        "id": 170,
                        "email": "int-train9012@yopmail.com",
                        "name_title": "Mr",
                        "first_name": "veftor",
                        "last_name": "k",
                        "file_name": null,
                        "phone": "8050284789",
                        "url": "https://tracksafety-dev.s3.amazonaws.com/blank-4px7pBY5DA-QAHS9cqWTj.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAVYLUBLBZTZO4EZNR%2F20200522%2Fus-east-1%2Fs3%2Faws4_request&X-Amz-Date=20200522T070759Z&X-Amz-Expires=3600&X-Amz-SignedHeaders=host&X-Amz-Signature=4f1972f7461f49362561cdf669123af6fed07163ca2cdef68334485e76ad87a1",
                        "is_deleted": false,
                        "is_active": true
                    },
                    "location": {
                        "id": 25,
                        "address_1": "GR-GrandStreet",
                        "address_2": "Leiccal Circle",
                        "city": "Bengaluru",
                        "zip_code": null,
                        "country": "ind",
                        "state": "Karantaka",
                        "lat_long": {
                            "lat": 123.444,
                            "long": 94.0949494
                        },
                        "type": 4,
                        "is_deleted": false,
                        "user": 108,
                        "organization": 72
                    },
                    "attendees": {
                        "max_participants": 20,
                        "accepted": 0,
                        "pending": 0,
                        "declined": 0,
                        "vacancy": 20,
                        "waiting_list": 0
                    },
                    "is_manual_entry": false
                },
                {
                    "id": 88,
                    "event_id": "EVE-0006",
                    "training_record": null,
                    "user": 108,
                    "event_role": "Admin",
                    "course": {
                        "id": 140,
                        "course_id": "COU-123",
                        "name": "React Dev-III Tools",
                        "description": "course",
                        "mode": "Online",
                        "type": "Certification",
                        "duration": 30,
                        "validity": 12,
                        "auth_by": "auth",
                        "license": true,
                        "has_cert": true,
                        "language": null,
                        "is_deleted": false,
                        "is_archived": false,
                        "user": 108,
                        "organization": 72
                    },
                    "organization": 72,
                    "training_status": null,
                    "type": "Training",
                    "mode": "Online",
                    "state": "Scheduled",
                    "trainer_status": "pending",
                    "reminder": 30,
                    "start_date": "Jan 02 2020",
                    "end_date": "Jun 02 2020",
                    "start_time": "08:30 AM",
                    "end_time": "06:30 PM",
                    "lat_long": null,
                    "max_participants": 20,
                    "trainer": {
                        "id": 170,
                        "email": "int-train9012@yopmail.com",
                        "name_title": "Mr",
                        "first_name": "veftor",
                        "last_name": "k",
                        "file_name": null,
                        "phone": "8050284789",
                        "url": "https://tracksafety-dev.s3.amazonaws.com/blank-4px7pBY5DA-QAHS9cqWTj.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAVYLUBLBZTZO4EZNR%2F20200522%2Fus-east-1%2Fs3%2Faws4_request&X-Amz-Date=20200522T070759Z&X-Amz-Expires=3600&X-Amz-SignedHeaders=host&X-Amz-Signature=4f1972f7461f49362561cdf669123af6fed07163ca2cdef68334485e76ad87a1",
                        "is_deleted": false,
                        "is_active": true
                    },
                    "location": {
                        "id": 25,
                        "address_1": "GR-GrandStreet",
                        "address_2": "Leiccal Circle",
                        "city": "Bengaluru",
                        "zip_code": null,
                        "country": "ind",
                        "state": "Karantaka",
                        "lat_long": {
                            "lat": 123.444,
                            "long": 94.0949494
                        },
                        "type": 4,
                        "is_deleted": false,
                        "user": 108,
                        "organization": 72
                    },
                    "attendees": {
                        "max_participants": 20,
                        "accepted": 0,
                        "pending": 0,
                        "declined": 0,
                        "vacancy": 20,
                        "waiting_list": 0
                    },
                    "is_manual_entry": false
                }
            ],
            "paginator": {
                "page_num": "1",
                "items": "100",
                "count": "4"
            }
        }
    }

```

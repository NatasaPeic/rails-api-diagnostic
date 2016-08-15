# Rails API Diagnostic

Place your responses inside the fenced code-blocks where indicated by comments.


What is the purpose of a backend?

```bash
To store data and interact with front end.
```

Which layer in the MVC pattern is used by the controller to fetch data?

```bash
Model.
```

In which part of the MVC pattern can we find C.R.U.D actions?

```bash
// your response here
```
List at least 5 standard actions that C.R.U.D corresponds to?

```bash
index, show, create, update, destroy
```

A user action fires a `PATCH` request for `pets/1`. Explain in detail each step
required for data to be returned to the client. (bullet points or ordered list,
please include information on dynamic segments, the params hash and seralizers).

```bash

- localhost:3000/pets/1
PATCH request is sent to the API. It is received by router.


- Router fires up UPDATE method and ask controller for the action.

patch '/pets/:id' to: '/pets#update'

- Controller holds the UPDATE method. UPDATE method needs data that model Pet holds.

def update

  if @pet.update(pet_params)
    head :no_content
  else
    render json: @pet.errors, status: :unprocessable_entity
  end
end

- Model holds bussiness logic. It pulls data that is needed for UPDATE method and sends it back to the controller. Controller sends it back to the router. Once the page is refreshed, we will be able to see our json.

- We can run serializer to be able show what we want from our model.

rails g serializer pet

class PetSerializer < ActiveModel::Serializer
  attributes :id, :name, :color, :age
end




-

```

What is the command to scaffold a `medicalRecords` join table which holds
refrences to a `pets` and a `vets` table?

```bash
rails g scaffold medicalRecords pet:references vet:references
```

What is the point of having a join table?

```bash
To be able to create many-to-many relationship between two datasets and to relate one to another.
```

Give an example of a one-to-many relationship and a many-to-many relationship:

```bash
One-to-many: Patients - Doctor (one doctor have many patients)

Many-to_many: Patients - Doctor through Appointments (one doctor have many patients, and one patient have many docotors through appointment join table. Appointment join table will refrence both docors and patients -- patient_id, doctor_id. Appointment join table can include other data too like time, duration of the appointment etc.)
```

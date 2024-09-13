# Project Description

**QuickCareMD** is a **Django / React SPA** walk-in medical app designed to enhance patient-doctor interactions and improve hospital workflow. With QuickCareMD, doctors can efficiently manage patient visits by viewing assigned patients, prescribing medication, and automatically removing treated patients from their dashboard (Discharging them) and sending the report to the Administration. The app also empowers hospital / administrators to manage the doctor roster, adding or removing doctors as needed to keep operations running smoothly. QuickCare ensures patients receive timely care while maintaining a seamless and organized experience for both medical professionals and hospital staff.

## MVP

- As a Hospital / Admin, I want to be able to sign up and sign in.
- As a Hospital / admin, When I log in, I should see a list of all currently registered doctors.
- As a Hospiatal / Admin, I want to be able to hire doctors to my Hospital.
- As a hospiatal / Admin, I want to be able to fire doctors from the Hospital.
- As a Hospital / Admin, Any doctor removed should no longer have access to the app or patient information.
- As a doctor, I want to be able to sign in to the hospital once i am registered by the Admin
- As a doctor, I can view patient details, including name, diseases, and treatments.
- As a doctor, I can prescribe medication to the patient.
- As a doctor, once medication is prescribed, the patient will automatically be removed from my dashboard.

## Wireframe of the App

![Wireframe Quick Care MD App](Quick%20Care%20MD%20ERD%20table%20-%20Wireframe.jpg)

## ERD table for QuickCareMD app

![ERD Table](Quick%20Care%20MD%20ERD%20table%20-%20Quick%20Care%20MD%20ERD%20table.jpg)

<details>
  <summary>Click here to see the summary of ERD </summary>

![ERD Summary of the table](Quick%20Care%20MD%20ERD%20table%20-%20Summary%20of%20ERD.jpg)

</details>

## Django Models

<details>
    <summary> Click here to see some of the models in Django </summary>

```python
# Hospital / Admin Model
class Hospital(models.Model):
    name = models.CharField(max_length=100)
    address = models.CharField(max_length=255)
    password = models.CharField(max_length=255)
    has_patients_or_doctors = models.BooleanField(default=False)  # Prevent hospital closure if patients or doctors exist

    def __str__(self):
        return self.name


# Doctor Model
class Doctor(models.Model):
    doctor_name = models.CharField(max_length=100)
    doctor_password = models.CharField(max_length=255)
    hospital = models.ForeignKey(Hospital, on_delete=models.CASCADE)

    def __str__(self):
        return self.doctor_name
```

</details>

## Component Diagram

<details>
<summary> Click here to see component diagram</summary>

![Diagram](Component%20Hiearchy%20Diagram.png)

</details>

## Path Table (Django)

- **Unprotected Routes:**

  - `/` - Home
  - `/login/` - Login
  - `/register/` - Register a doctor

- **Protected Routes:**
  - `/doctors/` - List of doctors
  - `/doctors/<int:id>/` - Doctor detail
  - `/patients/` - List of patients
  - `/patients/<int:id>/` - Patient detail
  - `/patients/admit/` - Admit a patient
  - `/diseases/` - List of diseases
  - `/diseases/<int:id>/` - Disease detail
  - `/treatments/` - List of treatments
  - `/treatments/create/` - Create a treatment
  - `/treatments/update/<int:id>/` - Update a treatment
  - `/patients/<int:patient_id>/discharge/` - Discharge a patient
  - `/discharges/` - List of discharged patients
  - `/users/verify/` - Verify user

## MVP Stretch Goals

- As a Hospital / Admin, I want to see a list of discharged patients.
- As a doctor, I want to have access to the list of discharged patients for record keeping.
- As a Hospital / Admin, I want to be able to hire nurses assigned to a doctor to delegate tasks.
- As a Hospita / Admin I want to be able to evaluate the performance of my doctors.

## Plan of Attack

|      Day       |               Task               |
| :------------: | :------------------------------: |
|  13th Friday   |   Create and present proposal    |
| 14th Saturday  |    Create backend structures     |
|  15th Sunday   |      Time Off /Research API      |
|  16th Monday   | Begin functions/ Launch Back End |
|  17th Tuesday  |         Finalize Backend         |
| 18th Wednesday |         Begin Front End          |
| 19th Thursday  |        Continue Front End        |
|  20th Friday   |   Overview and launch project    |
| 21st Saturday  |        Finalize Front End        |
|  22nd Sunday   |             Time Off             |
|  23rd Monday   |    Add CSS/ launch front end     |
|  24th Tuesday  |       Review Stretch Goals       |
| 25th Wednesday |         Presentation Day         |

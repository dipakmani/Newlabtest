import pandas as pd
import random
from faker import Faker

fake = Faker()

# -------------------------
# Define Dimension Lookups
# -------------------------

tests = [
    (1, "Complete Blood Count", "Blood", "Hematology", "4.0-10.0"),
    (2, "Urine Routine", "Urine", "Pathology", "Normal"),
    (3, "Chest X-Ray", "Imaging", "Radiology", "Clear/Abnormal"),
]

samples = [
    (1, "Blood", "Venipuncture", "Vacutainer", "2-8°C"),
    (2, "Urine", "Midstream", "Sterile Cup", "Room Temp"),
    (3, "Saliva", "Direct", "Sterile Tube", "Frozen"),
]

technicians = [
    (1, fake.name(), 5, "Morning", fake.phone_number()),
    (2, fake.name(), 8, "Evening", fake.phone_number()),
    (3, fake.name(), 3, "Night", fake.phone_number()),
]

equipments = [
    (1, "Hematology Analyzer", "Analyzer", "Siemens", "X200"),
    (2, "MRI Scanner", "MRI", "GE", "Optima360"),
    (3, "CT Scanner", "CT", "Philips", "Brilliance64"),
]

reports = [
    (1, "Pending", "2025-08-15", "Online", "Awaiting Approval"),
    (2, "Completed", "2025-08-14", "Offline", "Normal"),
    (3, "Completed", "2025-08-13", "Online", "Abnormalities Found"),
]

billings = [
    (1, 2000, 1500, "Card", 500),
    (2, 500, 500, "Cash", 0),
    (3, 7000, 7000, "Insurance", 0),
]

insurances = [
    (1, "HDFC Ergo", "Premium", 80, "Approved"),
    (2, "ICICI Lombard", "Basic", 60, "Pending"),
    (3, "Max Bupa", "Standard", 70, "Rejected"),
]

quality_checks = [
    (1, "Pass", "2025-08-14", fake.name(), "Good Sample"),
    (2, "Fail", "2025-08-13", fake.name(), "Contaminated"),
]

followups = [
    (1, "2025-08-20", fake.name(), "Physical"),
    (2, "2025-08-22", fake.name(), "Virtual"),
]

diagnosis = [
    (1, "Anemia", "D50", "Mild"),
    (2, "Diabetes", "E11", "Severe"),
]

conditions = [
    (1, "Hypertension", "Chronic", "High BP"),
    (2, "Asthma", "Chronic", "Allergens"),
]

medications = [
    (1, "Metformin", "500mg", "Twice Daily"),
    (2, "Paracetamol", "650mg", "As Needed"),
]

imaging = [
    (1, "X-Ray", "DICOM", "Server1"),
    (2, "MRI", "DICOM", "Server2"),
]

consent = [
    (1, "Written", "2025-08-12", "Signed"),
    (2, "Digital", "2025-08-14", "Pending"),
]

referrals = [
    (1, fake.name(), "Further Evaluation", "Cardiology"),
    (2, fake.name(), "Specialist Opinion", "Neurology"),
]

# -------------------------
# Generate Fact Table
# -------------------------

records = []
for i in range(20):  # generate 20 sample records
    test = random.choice(tests)
    sample = random.choice(samples)
    technician = random.choice(technicians)
    equipment = random.choice(equipments)
    report = random.choice(reports)
    billing = random.choice(billings)
    insurance = random.choice(insurances)
    qc = random.choice(quality_checks)
    followup = random.choice(followups)
    diag = random.choice(diagnosis)
    cond = random.choice(conditions)
    med = random.choice(medications)
    img = random.choice(imaging)
    con = random.choice(consent)
    ref = random.choice(referrals)

    records.append([
        # Test
        test[0], test[1], test[2], test[3], test[4],
        # Sample
        sample[0], sample[1], sample[2], sample[3], sample[4],
        # Technician
        technician[0], technician[1], technician[2], technician[3], technician[4],
        # Equipment
        equipment[0], equipment[1], equipment[2], equipment[3], equipment[4],
        # Report
        report[0], report[1], report[2], report[3], report[4],
        # Billing
        billing[0], billing[1], billing[2], billing[3], billing[4],
        # Insurance
        insurance[0], insurance[1], insurance[2], insurance[3], insurance[4],
        # Quality Check
        qc[0], qc[1], qc[2], qc[3], qc[4],
        # FollowUp
        followup[0], followup[1], followup[2], followup[3],
        # Diagnosis
        diag[0], diag[1], diag[2], diag[3],
        # Condition
        cond[0], cond[1], cond[2], cond[3],
        # Medication
        med[0], med[1], med[2], med[3],
        # Imaging
        img[0], img[1], img[2], img[3],
        # Consent
        con[0], con[1], con[2], con[3],
        # Referral
        ref[0], ref[1], ref[2], ref[3],
    ])

# Column Names
columns = [
    "TestID","Test_Name","Test_Type","Test_Category","Normal_Range",
    "SampleID","Sample_Type","Collection_Method","Sample_Container","Storage_Condition",
    "TechnicianID","Technician_Name","Technician_ExperienceYears","Technician_Shift","Technician_Contact",
    "LabEquipmentID","Equipment_Name","Equipment_Type","Manufacturer","Model",
    "ReportID","Report_Status","Generated_Date","Delivery_Mode","Remarks",
    "BillingID","Total_Charges","Amount_Paid","Payment_Method","Balance",
    "InsuranceID","Provider_Name","Plan_Type","Coverage_Percentage","Claim_Status",
    "QualityCheckID","QC_Status","QC_Date","QC_Technician","QC_Remarks",
    "FollowUpID","FollowUp_Date","FollowUp_Doctor","FollowUp_Type",
    "DiagnosisID","Diagnosis_Name","Diagnosis_Code","Severity_Level",
    "ConditionID","Condition_Name","Condition_Category","Risk_Factor",
    "MedicationID","Prescribed_Medicine","Dosage","Frequency",
    "ImagingID","Imaging_Type","Image_Format","Storage_Location",
    "ConsentID","Consent_Type","Consent_Date","Consent_Status",
    "ReferralID","Referring_Doctor","Referral_Reason","Referral_Department"
]

df = pd.DataFrame(records, columns=columns)

print(df.head(5))

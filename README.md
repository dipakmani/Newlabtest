import pandas as pd
import random

# ------------------------------
# Lookup Dictionaries for IDs
# ------------------------------

# 1. Tests
tests = {
    1: ("Blood Sugar", "Blood", "Biochemistry", "70-110 mg/dl"),
    2: ("Urine Culture", "Urine", "Microbiology", "Negative"),
    3: ("X-Ray Chest", "Imaging", "Radiology", "Normal"),
    4: ("Lipid Profile", "Blood", "Biochemistry", "Normal Range"),
    5: ("MRI Brain", "Imaging", "Radiology", "Normal")
}

# 2. Samples
samples = {
    1: ("Blood", "Venipuncture", "Vacutainer", "Refrigerated"),
    2: ("Urine", "Midstream", "Sterile Cup", "Room Temp"),
    3: ("Saliva", "Direct", "Sterile Tube", "Frozen")
}

# 3. Technicians
technicians = {
    1: ("John Doe", 5, "Morning", "9876543210"),
    2: ("Jane Smith", 8, "Night", "8765432109"),
    3: ("Amit Kumar", 3, "Evening", "7654321098")
}

# 4. Lab Equipment
equipments = {
    1: ("Hematology Analyzer", "Analyzer", "Siemens", "X200"),
    2: ("MRI Machine", "MRI", "GE", "Optima 360"),
    3: ("CT Scanner", "CT", "Philips", "Ingenuity")
}

# 5. Reports
reports = {
    1: ("Pending", "2025-08-01", "Online", "In Process"),
    2: ("Completed", "2025-08-05", "Offline", "All Clear")
}

# 6. Billing
billings = {
    1: (1000, 800, "Cash", 200),
    2: (5000, 5000, "Card", 0),
    3: (2000, 1500, "UPI", 500)
}

# 7. Insurance
insurances = {
    1: ("LIC Health", "Premium", 80, "Approved"),
    2: ("Star Health", "Basic", 50, "Pending"),
    3: ("HDFC Ergo", "Comprehensive", 90, "Approved")
}

# 8. Quality Check
qcs = {
    1: ("Pass", "2025-08-10", "John Doe", "OK"),
    2: ("Fail", "2025-08-09", "Jane Smith", "Recheck Required")
}

# 9. FollowUp
followups = {
    1: ("2025-08-20", "Dr. Mehta", "Physical"),
    2: ("2025-08-25", "Dr. Roy", "Virtual")
}

# 10. Diagnosis
diagnosis = {
    1: ("Diabetes Mellitus", "E11", "High"),
    2: ("Hypertension", "I10", "Medium"),
    3: ("Normal", "Z00", "Low")
}

# 11. Conditions
conditions = {
    1: ("Asthma", "Chronic", "Smoking"),
    2: ("Fever", "Acute", "Infection"),
    3: ("Heart Disease", "Chronic", "Obesity")
}

# 12. Medications
medications = {
    1: ("Paracetamol", "500mg", "Twice a day"),
    2: ("Metformin", "850mg", "Once a day"),
    3: ("Atorvastatin", "20mg", "Night")
}

# 13. Imaging
imagings = {
    1: ("X-Ray", "JPEG", "/storage/xray/"),
    2: ("MRI", "DICOM", "/storage/mri/"),
    3: ("CT", "TIFF", "/storage/ct/")
}

# 14. Consent
consents = {
    1: ("Written", "2025-08-01", "Approved"),
    2: ("Digital", "2025-08-02", "Approved")
}

# 15. Referral
referrals = {
    1: ("Dr. Sharma", "Specialist Opinion", "Cardiology"),
    2: ("Dr. Gupta", "Further Tests", "Neurology")
}

# ------------------------------
# Generate 5 Lakh Records
# ------------------------------
records = []
num_records = 500000

for i in range(1, num_records + 1):
    test_id = random.choice(list(tests.keys()))
    sample_id = random.choice(list(samples.keys()))
    technician_id = random.choice(list(technicians.keys()))
    equipment_id = random.choice(list(equipments.keys()))
    report_id = random.choice(list(reports.keys()))
    billing_id = random.choice(list(billings.keys()))
    insurance_id = random.choice(list(insurances.keys()))
    qc_id = random.choice(list(qcs.keys()))
    followup_id = random.choice(list(followups.keys()))
    diagnosis_id = random.choice(list(diagnosis.keys()))
    condition_id = random.choice(list(conditions.keys()))
    medication_id = random.choice(list(medications.keys()))
    imaging_id = random.choice(list(imagings.keys()))
    consent_id = random.choice(list(consents.keys()))
    referral_id = random.choice(list(referrals.keys()))

    record = {
        # Test
        "TestID": test_id,
        "Test_Name": tests[test_id][0],
        "Test_Type": tests[test_id][1],
        "Test_Category": tests[test_id][2],
        "Normal_Range": tests[test_id][3],

        # Sample
        "SampleID": sample_id,
        "Sample_Type": samples[sample_id][0],
        "Collection_Method": samples[sample_id][1],
        "Sample_Container": samples[sample_id][2],
        "Storage_Condition": samples[sample_id][3],

        # Technician
        "TechnicianID": technician_id,
        "Technician_Name": technicians[technician_id][0],
        "Technician_ExperienceYears": technicians[technician_id][1],
        "Technician_Shift": technicians[technician_id][2],
        "Technician_Contact": technicians[technician_id][3],

        # Lab Equipment
        "LabEquipmentID": equipment_id,
        "Equipment_Name": equipments[equipment_id][0],
        "Equipment_Type": equipments[equipment_id][1],
        "Manufacturer": equipments[equipment_id][2],
        "Model": equipments[equipment_id][3],

        # Report
        "ReportID": report_id,
        "Report_Status": reports[report_id][0],
        "Generated_Date": reports[report_id][1],
        "Delivery_Mode": reports[report_id][2],
        "Remarks": reports[report_id][3],

        # Billing
        "BillingID": billing_id,
        "Total_Charges": billings[billing_id][0],
        "Amount_Paid": billings[billing_id][1],
        "Payment_Method": billings[billing_id][2],
        "Balance": billings[billing_id][3],

        # Insurance
        "InsuranceID": insurance_id,
        "Provider_Name": insurances[insurance_id][0],
        "Plan_Type": insurances[insurance_id][1],
        "Coverage_Percentage": insurances[insurance_id][2],
        "Claim_Status": insurances[insurance_id][3],

        # QC
        "QualityCheckID": qc_id,
        "QC_Status": qcs[qc_id][0],
        "QC_Date": qcs[qc_id][1],
        "QC_Technician": qcs[qc_id][2],
        "QC_Remarks": qcs[qc_id][3],

        # Follow Up
        "FollowUpID": followup_id,
        "FollowUp_Date": followups[followup_id][0],
        "FollowUp_Doctor": followups[followup_id][1],
        "FollowUp_Type": followups[followup_id][2],

        # Diagnosis
        "DiagnosisID": diagnosis_id,
        "Diagnosis_Name": diagnosis[diagnosis_id][0],
        "Diagnosis_Code": diagnosis[diagnosis_id][1],
        "Severity_Level": diagnosis[diagnosis_id][2],

        # Condition
        "ConditionID": condition_id,
        "Condition_Name": conditions[condition_id][0],
        "Condition_Category": conditions[condition_id][1],
        "Risk_Factor": conditions[condition_id][2],

        # Medication
        "MedicationID": medication_id,
        "Prescribed_Medicine": medications[medication_id][0],
        "Dosage": medications[medication_id][1],
        "Frequency": medications[medication_id][2],

        # Imaging
        "ImagingID": imaging_id,
        "Imaging_Type": imagings[imaging_id][0],
        "Image_Format": imagings[imaging_id][1],
        "Storage_Location": imagings[imaging_id][2],

        # Consent
        "ConsentID": consent_id,
        "Consent_Type": consents[consent_id][0],
        "Consent_Date": consents[consent_id][1],
        "Consent_Status": consents[consent_id][2],

        # Referral
        "ReferralID": referral_id,
        "Referring_Doctor": referrals[referral_id][0],
        "Referral_Reason": referrals[referral_id][1],
        "Referral_Department": referrals[referral_id][2],
    }

    records.append(record)

# Convert to DataFrame
df = pd.DataFrame(records)

# Save to CSV
df.to_csv("Fact_LabTests.csv", index=False)

print("✅ Fact_LabTests.csv with 5 lakh records generated successfully!")

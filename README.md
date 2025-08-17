import pandas as pd
import numpy as np
from faker import Faker

fake = Faker()

# Number of records
n = 500000  

# --- ID Columns + Related Attributes ---
data = {
    # Operation and Visit linkage
    "OperationID": np.arange(1, n+1),
    "VisitID": np.random.randint(100000, 200000, n),

    # Procedure
    "ProcedureID": np.random.randint(1000, 2000, n),
    "Procedure_Type": np.random.choice(["Cardiac", "Orthopedic", "Neurology", "General Surgery", "ENT"], n),
    "Procedure_Category": np.random.choice(["Major", "Minor", "Critical"], n),
    "Procedure_CPT_Code": np.random.choice(["CPT1001", "CPT2002", "CPT3003", "CPT4004"], n),

    # Anesthesia
    "AnesthesiaID": np.random.randint(2000, 3000, n),
    "Anesthesia_Type": np.random.choice(["General", "Local", "Regional", "Sedation"], n),
    "Anesthesia_Dosage": np.random.randint(50, 200, n),
    "Anesthesia_Complications": np.random.choice(["Y", "N"], n),

    # Equipment
    "EquipmentID": np.random.randint(3000, 4000, n),
    "Equipment_Name": np.random.choice(["Scalpel", "Monitor", "ECG Machine", "Ventilator"], n),
    "Equipment_Type": np.random.choice(["Surgical", "Monitoring", "Life Support"], n),
    "Equipment_Manufacturer": np.random.choice(["GE", "Philips", "Siemens", "Medtronic"], n),
    "Equipment_Model": np.random.choice(["M100", "X200", "V300", "S400"], n),

    # Nurse
    "NurseID": np.random.randint(4000, 5000, n),
    "Nurse_FullName": [fake.name() for _ in range(n)],
    "Nurse_Shift": np.random.choice(["Day", "Night"], n),
    "Nurse_ExperienceYears": np.random.randint(1, 30, n),
    "Nurse_Education": np.random.choice(["B.Sc Nursing", "M.Sc Nursing", "Diploma"], n),

    # Room
    "RoomID": np.random.randint(5000, 6000, n),
    "Room_Type": np.random.choice(["ICU", "General", "Operation Theater"], n),

    # Blood Transfusion
    "BloodTransfusionID": np.random.randint(6000, 7000, n),
    "Blood_Type": np.random.choice(["A+", "A-", "B+", "B-", "AB+", "O+", "O-"], n),
    "Units_Transfused": np.random.randint(0, 5, n),
    "Donor_ID": np.random.randint(10000, 20000, n),
    "Transfusion_Complications": np.random.choice(["Yee", "No"], n),

    # Billing
    "BillingID": np.random.randint(7000, 8000, n),
    "Total_Charges": np.random.randint(5000, 50000, n),
    "Amount_Paid": np.random.randint(2000, 50000, n),
    "Payment_Method": np.random.choice(["Cash", "Credit Card", "Insurance", "UPI"], n),
    "Outstanding_Balance": np.random.randint(0, 10000, n),

    # Recovery
    "RecoveryID": np.random.randint(8000, 9000, n),
    "Recovery_Room_Type": np.random.choice(["ICU", "Ward", "Step-down"], n),
    "Recovery_DurationHours": np.random.randint(1, 120, n),
    "Recovery_Complications": np.random.choice(["Yes", "No"], n),
    "Physiotherapy_Required": np.random.choice(["Yes", "No"], n),

    # FollowUp
    "FollowUpID": np.random.randint(9000, 10000, n),
    "FollowUp_Date": [fake.date_between(start_date="-1y", end_date="today") for _ in range(n)],
    "FollowUp_Doctor": [fake.name() for _ in range(n)],
    "FollowUp_Type": np.random.choice(["Physical", "Virtual"], n),
    "Next_Appointment_Date": [fake.date_between(start_date="today", end_date="+6m") for _ in range(n)],

    # --- Measures ---
    "Operation_DurationMinutes": np.random.randint(30, 600, n),
    "Operation_Cost": np.random.randint(10000, 200000, n),
    "Complications_Flag": np.random.choice(["Yes", "No"], n),
    "Success_Rate": np.random.randint(60, 100, n),
    "Mortality_Flag": np.random.choice(["Yes", "No"], n)
}

# Create DataFrame
df = pd.DataFrame(data)

# Save to CSV
df.to_csv("fact_operations.csv", index=False)

print("✅ fact_operations.csv generated with", n, "records")

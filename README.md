aim_template.py

import streamlit as st
from datetime import date

st.set_page_config(
    page_title="Collaboration Hub | Aim Builder",
    page_icon="🎯"
)

st.title("🎯 Developing your aim")

st.write(
    "Complete the sections below to build your improvement aim."
)

st.header("1. Why?")

st.write("What are you trying to improve?")

improve_health = st.checkbox("Improve health outcomes")

improve_experience = st.checkbox("Improve patient experience")

improve_colleague = st.checkbox("Improve colleague satisfaction")

lower_costs = st.checkbox("Lower costs")

st.header("2. What?")

direction = st.radio(
    "What type of change are you aiming for?",
    ["Improve", "Increase", "Decrease"]
)

measure_name = st.text_input(
    "What do you want to change?",
    placeholder="e.g. average waiting time"
)

st.header("3. For whom?")

stakeholder = st.text_input(
    "Who is affected by the improvement?",
    placeholder="e.g. patients attending the Surgical Decisions Unit"
)

st.header("4. How much?")

baseline = st.text_input(
    "What is the current position?",
    placeholder="e.g. 120 minutes"
)

target = st.text_input(
    "What is the target?",
    placeholder="e.g. 90 minutes"
)

st.header("5. By when?")

target_date = st.date_input(
    "Select your target date",
    value=date.today()
)

st.divider()

st.header("Your Aim Statement")

if measure_name and stakeholder and baseline and target:

    aim_statement = (
        f"We will {direction.lower()} {measure_name} "
        f"for {stakeholder} "
        f"from {baseline} to {target} "
        f"by {target_date.strftime('%d/%m/%Y')}."
    )

    st.success(aim_statement)

else:

    st.info(
        "Complete the fields above to generate your aim statement."
    )

    import streamlit as st
from datetime import date


st.set_page_config(
    page_title="Collaboration Hub | Aim Builder",
    page_icon="🎯"
)


st.title("🎯 Developing your aim")

st.write(
    "Complete the sections below to build your improvement aim."
)


# WHY

st.header("1. Why?")

st.write("What are you trying to improve?")

improve_health = st.checkbox("Improve health outcomes")

improve_experience = st.checkbox("Improve patient experience")

improve_colleague = st.checkbox("Improve colleague satisfaction")

lower_costs = st.checkbox("Lower costs")


# WHAT

st.header("2. What?")

direction = st.radio(
    "What type of change are you aiming for?",
    ["Improve", "Increase", "Decrease"]
)

measure_name = st.text_input(
    "What do you want to change?",
    placeholder="e.g. average waiting time"
)


# FOR WHOM

st.header("3. For whom?")

stakeholder = st.text_input(
    "Who is affected by the improvement?",
    placeholder="e.g. patients attending the Surgical Decisions Unit"
)


# HOW MUCH

st.header("4. How much?")

baseline = st.text_input(
    "What is the current position?",
    placeholder="e.g. 120 minutes"
)

target = st.text_input(
    "What is the target?",
    placeholder="e.g. 90 minutes"
)


# BY WHEN

st.header("5. By when?")

target_date = st.date_input(
    "Select your target date",
    value=date.today()
)


# AIM STATEMENT

st.divider()

st.header("Your Aim Statement")

if measure_name and stakeholder and baseline and target:

    aim_statement = (
        f"We will {direction.lower()} {measure_name} "
        f"for {stakeholder} "
        f"from {baseline} to {target} "
        f"by {target_date.strftime('%d/%m/%Y')}."
    )

    st.success(aim_statement)

else:

    st.info(
        "Complete the fields above to generate your aim statement."
    )

    

import streamlit as st
from datetime import date


st.set_page_config(
    page_title="Developing your aim",
    page_icon="🎯",
    layout="wide"
)


# ---------------------------------------------------------
# CUSTOM STYLING
# ---------------------------------------------------------

st.markdown("""
<style>

/* Main page */
.stApp {
    background-color: #ffffff;
}

/* Reduce blank space at top */
.block-container {
    padding-top: 2rem;
    max-width: 1200px;
}

/* Main heading */
h1 {
    color: #1f4e79;
    font-size: 42px !important;
    font-weight: 700 !important;
}

/* Section headings */
h2 {
    color: #1f4e79;
    margin-top: 10px !important;
}

/* Input boxes */
div[data-baseweb="input"] {
    border-radius: 8px;
}

/* Aim result */
.aim-box {
    background-color: #eaf3f8;
    border-left: 8px solid #1f4e79;
    border-radius: 10px;
    padding: 24px;
    margin-top: 25px;
    font-size: 22px;
    font-weight: 600;
    color: #16324f;
}

</style>
""", unsafe_allow_html=True)


# ---------------------------------------------------------
# TITLE
# ---------------------------------------------------------

st.title("Developing your aim")

st.write(
    "Work through each section to create your improvement aim."
)


# ---------------------------------------------------------
# WHY?
# ---------------------------------------------------------

st.header("WHY?")

col1, col2 = st.columns(2)

with col1:
    health = st.checkbox("Improve health outcomes")
    experience = st.checkbox("Improve patient experience")

with col2:
    colleague = st.checkbox("Improve colleague satisfaction")
    costs = st.checkbox("Lower costs")


# ---------------------------------------------------------
# WHAT?
# ---------------------------------------------------------

st.header("WHAT?")

direction = st.radio(
    "What kind of improvement are you making?",
    ["Improve", "Increase", "Decrease"],
    horizontal=True
)

what = st.text_input(
    "What are you trying to change?",
    placeholder="e.g. average waiting time"
)


# ---------------------------------------------------------
# FOR WHOM?
# ---------------------------------------------------------

st.header("FOR WHOM?")

who = st.text_input(
    "Who will benefit?",
    placeholder="e.g. patients attending the Surgical Decisions Unit"
)


# ---------------------------------------------------------
# SYSTEM / SCOPE
# ---------------------------------------------------------

st.header("SYSTEM / SCOPE")

scope = st.text_input(
    "Where will the improvement happen?",
    placeholder="e.g. Surgical Decisions Unit"
)


# ---------------------------------------------------------
# HOW MUCH?
# ---------------------------------------------------------

st.header("HOW MUCH?")

current_col, arrow_col, target_col = st.columns([5, 1, 5])

with current_col:
    current = st.text_input(
        "Current position",
        placeholder="e.g. 120 minutes"
    )

with arrow_col:
    st.markdown(
        "<div style='text-align:center; padding-top:35px;"
        "font-size:30px;'>→</div>",
        unsafe_allow_html=True
    )

with target_col:
    target = st.text_input(
        "Target",
        placeholder="e.g. 90 minutes"
    )


# ---------------------------------------------------------
# BY WHEN?
# ---------------------------------------------------------

st.header("BY WHEN?")

target_date = st.date_input(
    "Target date",
    value=None
)


# ---------------------------------------------------------
# BUILD THE AIM
# ---------------------------------------------------------

st.divider()

st.subheader("OUR AIM")

if what and who and current and target and target_date:

    formatted_date = target_date.strftime("%d/%m/%Y")

    aim = (
        f"We will {direction.lower()} {what} "
        f"for {who}"
    )

    if scope:
        aim += f" within {scope}"

    aim += (
        f" from {current} to {target} "
        f"by {formatted_date}."
    )

    st.markdown(
        f'<div class="aim-box">{aim}</div>',
        unsafe_allow_html=True
    )

else:

    st.info(
        "Complete the sections above to generate your aim."
    )

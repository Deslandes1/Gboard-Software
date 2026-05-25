import streamlit as st
from streamlit_drawable_canvas import st_canvas

# 1. Page Configuration Engine
st.set_page_config(
    page_title="THE BOARD SOFTWARE | GLOBALINTERNET.PY",
    page_icon="🎨",
    layout="wide",
    initial_sidebar_state="expanded"
)

# 2. Custom CSS Injection for Theme Isolation
st.markdown(
    """
    <style>
    .stApp {
        background-color: #0f172a;
        color: #f8fafc;
    }
    .main-title {
        text-align: center;
        font-weight: 800;
        font-size: 2.2rem;
        background: linear-gradient(90deg, #38bdf8, #34d399, #fbbf24);
        -webkit-background-clip: text;
        -webkit-text-fill-color: transparent;
        margin-bottom: 2px;
    }
    .sub-title {
        text-align: center;
        font-size: 0.9rem;
        color: #94a3b8;
        margin-bottom: 15px;
    }
    div[data-testid="stSidebar"] {
        background-color: #1e293b !important;
        border-right: 1px solid #334155;
    }
    </style>
    """,
    unsafe_allow_html=True
)

# Title Header
st.markdown('<h1 class="main-title">THE BOARD SOFTWARE</h1>', unsafe_allow_html=True)
st.markdown('<p class="sub-title">Engineered by GlobalInternet.py | Touch, Pen, and Stylus Canvas Core</p>', unsafe_allow_html=True)

# =========================================================================
# 🎛️ SIDEBAR CONTROL FRAMEWORK
# =========================================================================
st.sidebar.markdown("### 🛠️ Board Configuration")

# Tool selection Matrix
drawing_mode = st.sidebar.selectbox(
    "Select Input / Writing Tool:",
    ("freedraw", "line", "rect", "circle", "transform"),
    index=0,
    help="Use 'freedraw' for finger/pen text writing. Use 'transform' to select, move, resize, or delete elements."
)

st.sidebar.markdown("---")

# Pen & Pencil Brush Color Swatches
stroke_color = st.sidebar.color_picker("🎨 Select Pen / Pencil Color:", "#34d399")

# Board Canvas Background Control
bg_color = st.sidebar.color_picker("🧱 Select Board Background Color:", "#111827")

# Thickness Calibration
stroke_width = st.sidebar.slider("✏️ Line / Stroke Thickness:", min_value=1, max_value=30, value=4)

st.sidebar.markdown("---")
st.sidebar.markdown("### 💡 Quick Instructions:")
st.sidebar.info(
    "1. **Write/Draw:** Choose 'freedraw' and use your finger, pen, mouse, or pencil directly on the board.\n\n"
    "2. **Modify/Erase:** Switch tool mode to **'transform'**. Click on any drawn line or text writing to move it, stretch it, or press the **Delete / Backspace** key on your keyboard to wipe it out permanently!"
)

# =========================================================================
# 🎨 CENTRAL INTERACTIVE BOARD CANVAS
# =========================================================================

# Create responsive columns to center-align the board perfectly
canvas_col, info_col = st.columns([5, 1])

with canvas_col:
    # Drawing Canvas Initialization
    canvas_result = st_canvas(
        fill_color="rgba(255, 255, 255, 0.0)",  # Transparent shapes by default
        stroke_width=stroke_width,
        stroke_color=stroke_color,
        background_color=bg_color,
        update_穩定=True,
        height=520,
        drawing_mode=drawing_mode,
        key="board_canvas",
    )

with info_col:
    st.markdown("#### 📊 Canvas Data")
    if canvas_result.json_data is not None:
        objects_count = len(canvas_result.json_data["objects"])
        st.metric(label="Active Elements", value=objects_count)
        
        if objects_count > 0:
            st.success("Board active. Streamlit rendering engine operational.")
        else:
            st.caption("Board is empty. Ready for writing.")

# =========================================================================
# 📜 FOOTER BASE NODE
# =========================================================================
st.markdown(
    """
    <div style="text-align: center; margin-top: 20px; font-size: 0.8rem; color: #475569; border-top: 1px solid #1e293b; padding-top: 10px;">
        © 2026 GLOBALINTERNET.PY | Advanced Custom Drawing Software Pipelines.
    </div>
    """,
    unsafe_allow_html=True
)

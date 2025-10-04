import moviepy.editor as mp

# Replace with your actual file paths
video1_path = "20250917_210716.mov"
video2_path = "FacetuneD598F2BB-D7C6-47B5-820F-A19DD94110E2.mov"

# Load the two main videos
video1 = mp.VideoFileClip(video1_path)
video2 = mp.VideoFileClip(video2_path)

# --- Version A: replicate sample transition ---
# Smooth crossfade between videos
merged_crossfade = mp.concatenate_videoclips(
    [video1, video2.crossfadein(1.5)], method="compose"
)

# --- Version B: personalized Disney fireworks touch ---
# Fade out first video, fade in second video
personalized = mp.concatenate_videoclips(
    [video1.fadeout(1.5), video2.fadein(1.5)], method="compose"
)

# Export both videos
merged_crossfade.write_videofile("proposal_transition_same.mp4", codec="libx264", audio_codec="aac")
personalized.write_videofile("proposal_transition_personalized.mp4", codec="libx264", audio_codec="aac")


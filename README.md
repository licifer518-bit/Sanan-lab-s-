# Sanan-lab-s-# Sanan-lab-s-
"use client";
import { useState } from "react";

export default function SananLabsUI() {
  const [videoUrl, setVideoUrl] = useState(null);
  const [loading, setLoading] = useState(false);

  const handleGenerate = async (userPrompt) => {
    setLoading(true);
    const response = await fetch("/api/generate", {
      method: "POST",
      body: JSON.stringify({ prompt: userPrompt }),
    });

    if (response.ok) {
      const blob = await response.blob();
      const url = URL.createObjectURL(blob);
      setVideoUrl(url); // This shows the video in your gallery
    }
    setLoading(false);
  };

  return (
    // Your Sanan Lab's UI code here...
    <button onClick={() => handleGenerate(prompt)}>
       {loading ? "Sanan Lab's is thinking..." : "Generate AI Video"}
    </button>
  );
}

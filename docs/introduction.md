import React, { useState } from "react";
import { View, Text, TouchableOpacity, StyleSheet } from "react-native";
import { Ionicons } from "@expo/vector-icons";

export default function MeditationGame() {
  const [score, setScore] = useState(0);
  const [isPlaying, setIsPlaying] = useState(false);

  const startGame = () => {
    setScore(0);
    setIsPlaying(true);
    setTimeout(() => {
      setIsPlaying(false);
    }, 30000); // เล่น 30 วินาที
  };

  const increaseScore = () => {
    if (isPlaying) {
      setScore(score + 1);
    }
  };

  return (
    <View style={styles.container}>
      <Text style={styles.title}>เกมฝึกสมาธิ</Text>
      <Text style={styles.subtitle}>แตะที่หน้าจอเมื่อรู้สึกสงบ</Text>
      <Text style={styles.score}>คะแนน: {score}</Text>
      {isPlaying ? (
        <TouchableOpacity style={styles.button} onPress={increaseScore}>
          <Ionicons name="finger-print" size={50} color="white" />
          <Text style={styles.buttonText}>แตะที่นี่</Text>
        </TouchableOpacity>
      ) : (
        <TouchableOpacity style={styles.startButton} onPress={startGame}>
          <Text style={styles.startText}>เริ่มเกม</Text>
        </TouchableOpacity>
      )}
    </View>
  );
}

const styles = StyleSheet.create({
  container: {
    flex: 1,
    justifyContent: "center",
    alignItems: "center",
    backgroundColor: "#F5F5DC",
  },
  title: {
    fontSize: 24,
    fontWeight: "bold",
    marginBottom: 10,
  },
  subtitle: {
    fontSize: 16,
    color: "gray",
    marginBottom: 20,
  },
  score: {
    fontSize: 20,
    fontWeight: "bold",
    marginBottom: 20,
  },
  button: {
    flexDirection: "row",
    alignItems: "center",
    backgroundColor: "#6200EE",
    padding: 15,
    borderRadius: 10,
  },
  buttonText: {
    color: "white",
    fontSize: 18,
    marginLeft: 10,
  },
  startButton: {
    backgroundColor: "#28A745",
    padding: 15,
    borderRadius: 10,
  },
  startText: {
    color: "white",
    fontSize: 20,
  },
});

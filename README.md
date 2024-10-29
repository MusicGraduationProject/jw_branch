변경사항 

WelcomPage 

import SwiftUI

struct WelcomPage: View {
    var body: some View {
        NavigationView { // 네비게이션을 위한 NavigationView 추가
            VStack {
                // 상단의 제목 텍스트
                Text("Sample transformed")
                    .font(.largeTitle)
                    .bold()
                    .padding(.top, 40)
                    .foregroundColor(.white)
                
                Spacer()
                
                // 원형 배경과 이미지
                ZStack {
                    Circle()
                        .fill(LinearGradient(gradient: Gradient(colors: [Color.orange, Color.black]), startPoint: .top, endPoint: .bottom))
                        .frame(width: 200, height: 200)
                    
                    Image("Image") // Assets에 추가된 이미지 이름을 사용
                        .resizable()
                        .scaledToFit()
                        .frame(width: 150, height: 150)
                        .clipShape(Circle())
                }
                
                Spacer()
                
                // 하단의 버튼
                NavigationLink(destination: MusicSelectView()) { // ResultView로 이동하는 링크 추가
                    Text("음악 만들기")
                        .font(.headline)
                        .padding()
                        .frame(maxWidth: .infinity)
                        .background(Color.white)
                        .foregroundColor(.black)
                        .cornerRadius(10)
                        .padding(.horizontal, 20)
                        .padding(.bottom, 40)
                }
            }
            .background(Color.gray)
            .edgesIgnoringSafeArea(.all)
        }
    }
}

struct ResultView: View {
    var body: some View {
        VStack {
            Text("Transformed Result")
                .font(.largeTitle)
                .bold()
                .padding(.top, 40)
                .foregroundColor(.black)
            
            Spacer()
            
            // 결과 화면의 내용 (예: 텍스트, 이미지, 기타 UI 요소)
            Text("This is the transformed result.")
                .font(.title)
                .padding()
            
            Spacer()
        }
        .background(Color.white)
        .edgesIgnoringSafeArea(.all)
    }
}

#Preview {
    WelcomPage()
}



////////////////////////////
////////////////////////////
////////////////////////////

////////////////////////////



MusicPlayView


import SwiftUI
import AVFoundation

struct MusicPlayView: View {
    
    @State private var isRecording = false
    @State private var audioRecorder: AVAudioRecorder?
    @State private var audioPlayer: AVAudioPlayer?

    var body: some View {
        VStack(spacing: 20) {
            // Record Button
            Button(action: {
                if isRecording {
                    stopRecording()
                } else {
                    startRecording()
                }
            }) {
                Image(systemName: "record.circle")
                    .resizable()
                    .frame(width: 80, height: 80)
                    .foregroundColor(.red)
            }
            
            // Play and Save Buttons
            HStack(spacing: 40) {
                Button(action: playRecording) {
                    Image(systemName: "play.circle")
                        .resizable()
                        .frame(width: 40, height: 40)
                }
                Button(action: saveRecording) {
                    Image(systemName: "square.and.arrow.down")
                        .resizable()
                        .frame(width: 40, height: 40)
                }
            }

            Spacer() // This spacer pushes the following buttons to the bottom of the screen

            // Upload and Result Buttons
            HStack(spacing: 40) {
                Button(action: uploadMIDI) {
                    VStack {
                        Image(systemName: "icloud.and.arrow.up")
                            .resizable()
                            .frame(width: 40, height: 40)
                        Text("Upload MIDI")
                            .font(.caption)
                    }
                }
                
                Button(action: showResult) {
                    VStack {
                        Image(systemName: "music.note.list")
                            .resizable()
                            .frame(width: 40, height: 40)
                        Text("Result")
                            .font(.caption)
                    }
                }
            }
            .padding(.bottom, 20) // Add some padding at the bottom for better visual spacing
        }
        .padding()
        .onAppear(perform: setupRecorder)
    }
    
    // MARK: - Functions
    
    func setupRecorder() {
        // Configure audio session and prepare for recording
    }
    
    func startRecording() {
        isRecording = true
        // Start audio recording logic here
    }
    
    func stopRecording() {
        isRecording = false
        // Stop audio recording logic here
    }
    
    func playRecording() {
        // Audio playback logic here
    }
    
    func saveRecording() {
        // Saving recording logic here
    }
    
    func uploadMIDI() {
        // MIDI upload functionality here
    }
    
    func showResult() {
        // Show result functionality here
    }
}

#Preview {
    MusicPlayView()
}




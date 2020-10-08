# HLTTauProducerPhase2


cmsrel CMSSW_11_1_3

cd CMSSW_11_1_3/src

cmsenv

git cms-init

git cms-merge-topic -u cms-l1t-offline:l1t-phase2-v3.1.9

scram b -j 8

# tracking reconstruction configuration


git clone https://github.com/AdrianoDee/CMS_HLT_Phase2_Tracking -b configs

# workaround for PFSimParticle :: trackerSurfaceMomentum

 ref: hatakeyamak: FBaseSimEvent_ProtectAgainstMissingTrackerSurfaceMomentum


git cms-addpkg FastSimulation/Event

git remote add hatakeyamak https://github.com/hatakeyamak/cmssw.git

git fetch hatakeyamak

git cherry-pick 0cf67551731c80dc85130e4b8ec73c8f44d53cb0


git clone https://github.com/missirol/JMETriggerAnalysis.git -o missirol -b phase2

# fix for RecoPFTauQualityCuts to allow maxDeltaZToLeadTrack Used


git cms-merge-topic veelken:CMSSW_11_1_x_phase2HLT


# Tallinn-internal code for Phase-2 HLT trigger studies


git clone https://github.com/HEP-KBFI/hlttrigger-phase2hltpftaus $CMSSW_BASE/src/HLTrigger/Phase2HLTPFTaus

git clone https://github.com/HEP-KBFI/dataformats-phase2hltpftaus $CMSSW_BASE/src/DataFormats/Phase2HLTPFTaus

# To Reconstruct L1 HPS Tau


git clone https://github.com/sandeepbhowmik1/L1TauProducerPhase2 $CMSSW_BASE/src/L1Trigger/Phase2L1Taus

git clone https://github.com/sandeepbhowmik1/L1TauProducerPhase2-DataFormats $CMSSW_BASE/src/DataFormats/Phase2L1Taus

# Modification To compile


git cms-addpkg DataFormats/L1TCorrelator

cp /home/sbhowmik/L1TauTrigger/L1TauProducerPhase2/CMSSW_11_1_2/src/DataFormats/L1TCorrelator/interface/TkPrimaryVertex.h $CMSSW_BASE/src/DataFormats/L1TCorrelator/interface

cp /home/sbhowmik/L1TauTrigger/L1TauProducerPhase2/CMSSW_11_1_2/src/DataFormats/L1TCorrelator/src/classes_def.xml $CMSSW_BASE/src/DataFormats/L1TCorrelator/src


git cms-addpkg DataFormats/L1Trigger

cp /home/sbhowmik/L1TauTrigger/L1TauProducerPhase2/CMSSW_11_1_2/src/DataFormats/L1Trigger/interface/Muon.h $CMSSW_BASE/src/DataFormats/L1Trigger/interface

cp /home/sbhowmik/L1TauTrigger/L1TauProducerPhase2/CMSSW_11_1_2/src/DataFormats/L1Trigger/src/classes_def.xml $CMSSW_BASE/src/DataFormats/L1Trigger/src


scram b -j 8



# To update the installation instruction


git clone https://github.com/sandeepbhowmik1/HLTTauProducerPhase2

